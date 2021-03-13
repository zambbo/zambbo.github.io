---
layout: posts
categories: Algorithm
title: What is Dynamic Programming?
toc: true
toc_label: "about DP"
---

# What is Dynamic Programming?

## about DP
**Dynamic Programming(DP)** is an algorithm for solving optimization problems consist of same sub-problem.
We can solve entire of the problem using the optimal solution of sub-problem.

We already know **Fibonacci Numbers**.  Fibonacci Numbers denote form a sequence such that each number is the sum of the two preceding numbers.
We can implement this theorem with python
```python
    def fibo(n):
        if n<2:
            return 1
        return fibo(n-1) + fibo(n-2)
```
fibo(n) is the problem consist of fibo(n-1) and fibo(n-2). So We solve the problem with the sub-problem of original problem(DP)!

## Some problmes
There is some problem with previous Algorithm. If n becomes bigger and bigger, calculating counts of sub-problems are much bigger.
So, There are two methods for avoid this kind of problem.

## Top-down
In this approach, we try to solve bigger problem by recursively finding the solution to smaller sub-problems.
To avoid calculating values multiple times, we store intermediate calculations in a table.
The process of storing intermediate results is called **Memoization**
Let's see the code implementing Fibonacci Numbers with Top-down method.
```python
    mem = [-1 for x in range(11)]

    def fibo_memoization(n):
        global mem

        if n < 2:
            return 1
        
        if mem[n] >=0:
            return mem[n]
        mem[n] = fibo_memoization(n-1) + fibo_memoization(n-2)
        return mem[n]
    
    if __name__ == '__main__':
        print(fibo_memoization(10))
```
I use mem list to store the value of the result. So I can avoid re-calculating same sub-problems.
There is another method to solve this problem.

## Bottom-up
Bottom-up method is solving smaller problems to build a solution for bigger problem.
Merge-sort is good example for Bottom-up.

Let's see the code implementing Fibonacci Numbers with Bottom-up method.
```python
    def fibo_bottom_up(n):
        if n<2:
            return 1
        ret = 1
        prev = 1
        for idx in range(2,n+1):
            ret = ret+prev
            prev = ret-prev
        return ret
    if __name__ == '__main__':
        print(fibo_bottom_up(10))
```

## END
Dynamic Programming is useful to solve problem which consist of sub-problems.
**But** It is distinct from divide-and-conquer, as the divide-and-conquer 
approach works well if the sub-problems are essentially unique.
So we should apply this Algorithm when recursive problem have re-occur sub-problem.

