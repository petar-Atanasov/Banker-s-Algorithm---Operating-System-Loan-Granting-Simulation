# Banker's Algorithm - Operating System Loan Granting Simulation

## Overview

This project is a **C++ implementation of the Banker's Algorithn**, a classic resource allocation and deadlock avoidance algorithm used in **Operating Systems**.

The system simulates how an operating system decides whether it is safe to **gran resource requests (loans)** to processes without causing deadlock. It evaluates the current system state and ensures that all processes can still complete safely before approving any request.

This project demonstrates how a core operating systems concept can be translated into a working program that models **safe resource allocation**.

## Key Purpose

The purpose of this project is to:

- implement the **Banker#s Algorithm** in C++
- understand how operating systems prevent **deadlocks**
- simulate **resource allocation decissions**
- demonstrate how a system determines a **safe** or **usafe** state
- apply algorithmic thinking to a fundamental operating system problem

This project focuses on the **correctness and safety of resource allocation**, which is a key in operating system design.

## Problem Explained

In an operating system, multiple processes complete for limited resources such as:

- CPU time
- memory
- files
- I/O devices

If resources are allocated incorrectly, the system can enter a **deadlock state**, where processes wait indefinitely and none can continue.

The Banker's Algorithm avoits this by checking whether granting a request would keep the system in a **safe state**. If the request could lead to deadlock, it is denied.

This project simulates that behaviour using a **loan-granting model**, where processes request resources and the system decides whether the request can be safely granted.

## Project Execution

The program simulates a system with:

- multiple processes
- multiple resource types
- predifined maximum resource demands
- current resource allocations

It performs the following steps:

1. defines the available system resources
2. stores the current allocation for each process
3. stores the maximum demand for each process
4. calculates the remaining resource need
5. evaluates a resource request from a process
6. temporarily simulates allocation
7. runs the safety check
8. decides whether the request should be granted or denied.

## Core Algorithm - Banker's Algorithm

The main logic follows the Banker's Algorithm

### Key Data Structures

The system uses the standard structures associated with the algorithm:

- **Available** --> recources currently available
- **Max** --> maximum resources each process may request
- **Allocation** --> resources currently assigned to each process
- **Need** --> resources each process still requires to finish

```
Need = Max - Allocation
```

### Safety Algorithm

Before approving a request, the program checks whether the system remains in a **safe state**.

The safety algorithm works by:

1. starting with the currently available resources
2. finding a process whose remaining need can be satisfied
3. simulating that process finishing
4. releasing its allocated resources back into the pool
5. repeating until either:
   - all processes can finish --> **SAFE**
   - no further process can proceed --> **UNSAFE**

If every process can eventually complete, the system is considered safe.

### Resource Request Algorithm

When a process makes a request, the system performs these checks:

1. verify that the request does not exceed the process's remaining **Need**
2. verify that the request does not exceed the currectly **Available** resources
3. temporarily allocate the resources
4. run the safety algorithm
5. if the system reamins **safe**, grant the request
6. if the system becomes **unsafe**, roll back the temporary allocation and deny the request

## How the System Works

1. the system in initialised with resource and process data
2. maximum demands and current allocations are stored
3. the remaining need matrix is calculated
4. a resource request is evaluated
5. the system simulates the request
6. the safety algorithm checks whether all processes can still complete
7. the request is granted **only if the system remains safe**

## How to Run this Project

Clone the repository: 
```
```

Compile the C++ source files:

```
g++ *.cpp - o bankers
```

Run the program:
```
./bankers
```
