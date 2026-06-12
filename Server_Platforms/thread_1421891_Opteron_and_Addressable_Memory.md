---
title: "Opteron and Addressable Memory"
date: 2010-03-04
forum: Server Platforms
---

### Post by lflindsey on 2010-03-04
I'm having a hard time finding a direct answer to this question, so I'm going to pose it to you-all.  Suppose I'm running an AMD64 kernel on an Opteron machine with Direct-Connect Hypertransport NUMA buzzword buzzword.

Each physical processor has its own bank of memory - ie, if I have 32GB of ram in this machine with 8GB in each bank, each processor is attached directly to one of those banks of 8 gigs of RAM.

What is the maximum space addressable by a single process in this situation?  Could I theoretically address the entire 32GB, or am I restricted to the 8GB of a single bank?

Also, I'm wondering what the limitations are in the case of partial population.  In other words, is it possible to put only two processors in a 4-socket motherboard, and if so, does that limit the amount of usable ram in the system?

Thanks y'all.

---

### Post by miguel.antonio.168 on 2010-03-05
[SIZE=3]if you are using the ubuntu 64 version, your system can make use of that 32gb memory, unless if you have the ubuntu 386 version.

you can check your memory by typing this command in your terminal:[/SIZE]
[INDENT][SIZE=3]cat /proc/meminfo
[/SIZE][/INDENT][SIZE=3]what's the version release of your ubuntu? there was once an issue with the kernel that it can only address up to 3 gb of memory, we encountered it before and we just upgraded then to a new version of ubuntu and fixed it .[/SIZE]

---

### Post by lflindsey on 2010-03-05
It's not the total addressable space that I'm worried about.

For instance, in the old days it was possible to have more than 4GB of RAM on a 32-bit system, but the kernel had to play some paging tricks to make it work.  As a result, no one process (if I remember correctly) could address more than 4GB, or really 3GB in userland, even if you had much more than that installed.

What I'm wondering is if there is a similar scheme in a HyperTransport Opteron system.  Apparently, each physical processor is attached to its "own" bank of RAM that it has direct access to.

Can I run a single Linux process on one Opteron processor, and allocate an amount of RAM that is more than is available in that one bank?  I suspect that the answer is "yes," but I want to be sure before investing in such a system.

A secondary question is: what would happen if I were to install RAM in a bank that has no corresponding processor?  In other words, if I have a quad-socket mother board with only two installed processors, do I now have two banks that are useless, or are those still accessible to the installed processors?

---

