---
title: "Make Java Use more CPU's"
date: 2011-03-23
forum: Server Platforms
---

### Post by woodzykiler on 2011-03-23
i have ubunto 10_4 X86-64 (i use putty to connect
installed apps
screen
mysql server-client
my java program
open jdk* 64bit
apanche2 (the web server stuff)
and its aVPS machine
Xeon 2.0 64bit 4 GB ram
 
my question is how can i make (or force) my java program to use more then 1 core?
id like it to be useing just 5 of the 6 that i have i use a .sh to run it this is the code for it ```
#!/bin/bash 
cd "${0%/*}"; java -Xshare:auto -Xmx2662M -jar craft.jar
```
some one please help me in dieing here :(

---

### Post by Aaron44126 on 2011-03-23
Your Java program (or any other program for that matter) will not use more than one core unless it was programmed specifically to execute separate tasks in parallel.

---

### Post by woodzykiler on 2011-03-23
> **Aaron44126 said:**
> Your Java program (or any other program for that matter) will not use more than one core unless it was programmed specifically to execute separate tasks in parallel.
 
i would have to reright it to have it use more cores?
i know nothing about java but how hard could it be?

---

### Post by tgalati4 on 2011-03-23
The JAVA framework was written way before multicore processors became popular.  In order to be compatible across multiple platforms, one needs to make assumptions about processor/machine capabilities.  Multicore was not even in the picture during JAVA's inception.

---

### Post by doas777 on 2011-03-23
> **woodzykiler said:**
> i would have to reright it to have it use more cores?
i know nothing about java but how hard could it be?
yes.
at a fundemental level a processor runs "threads" (a process consists of one or more threads) and can only run one thread at a time (there are exceptions to this but they just muddy the concept).

a dual core or dual cpu rig is thus capable of running exactly the number of threads at the same time as it has processors.

a program that runs on a single thread must have it;s instructions run in a very precise order, so if two cores run bits of the same thread, they will not finish or begin in the order expected. for instance in the beginning of a thead a variable String TestText is declared and then used throughout the code. if the cpu finished executing the middle of the thread before the beginning, then the var woudl not even be declared yet from the threads perspective.

to make a program operate on multiple CPUs/Cores a program must break it;s tasks into isolated threads that can operate synchronously without producing an error in the process. 

for system optimizing, if you have a single thread process, and it goes too slow, buy a CPU with a higher frequency (Ghz), whereas for a multi-threaded process, increase the number of cores.

---

### Post by Vegan on 2011-03-23
I was an early developer for threads (parallel programming) that seems to still be not well understood.

I am very good with parallel programming using OpenMP and C++

Java is not a threaded language so you are out of luck

---

