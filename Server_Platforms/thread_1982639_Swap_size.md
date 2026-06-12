---
title: "Swap size?"
date: 2012-05-18
forum: Server Platforms
---

### Post by scottbomb on 2012-05-18
I'm reading the Ubuntu Server Guide. In the first few pages where it discusses installation, it says "A swap partition twice the size of available RAM capacity may not always be desirable, especially on systems with large amounts of RAM."

Why is this?

I have 8 GB of RAM on this machine. What difference does it make if swap is 4, 8, 16 GB?

---

### Post by hawkmage on 2012-05-18
With Linux you can get away with no swap space but if you run out of memory your system can crash.  

If you are running a server with a fairly constant amount of memory usage you can safely get away with 1/2 your physical memory.  If you are running things that fluctuate in memory usage or the services you are running will spawn more processes to hadle increased load you may want 1 to 2 times physical memory in swap. 

Another thing to keep in mind is that idle processes can be swapped out of memory allowing for using memory for caching IO to increase filesystem performance.  

In linux distros with a kernet 2.6 or later you can set the value of vm.swappiness from 0 to 100 to set how aggressive memory is swapped out.  I think Ubuntu defaults to about 60.

As with any tuning parameter it really depends on what you will be done with the system what is best for you.

---

### Post by David Andersson on 2012-05-18
The amount of ram and swap needed *depends on how the computer is used*. What programs, how often and intesively programs run, etc? It is hard to tell what is best for you without details, but I think the recommendation is good.

I think the recommendation assumes that a *situation* where swap twice the size of ram would be *needed* and *still offer good performance* is quite *unlikely*.

During any small time interval, all currently running programs will access a certain amount of virtual memory, called the "**working set**". It must be in ram for good performance. Parts of those programs virtual memory are not accessed for a while, and some programs may be sleeping, accessing no virtual memory at all during the time interval. Those parts of memory can be in swap with little impact on performance.

**In theory**, you estimate the worst case "working set" and decide the amount of ram based on that. Then you estimate the total amount of memory used by all simultaneous processes and decide the amount of swap based on that (swap=total - ram).

**In practice**, you start with a intelligent guess for the amount of ram, and create about the same amount of swap. Then you add more ram if the computer runs too slow.

In essence, make sure you have enough ram, and add swap according to guidelines.

---

### Post by scottbomb on 2012-05-19
Thank you, that all makes perfect sense. It sounds similar to managing swap size in Windows except for the fact that Windows doesn't use swap for hibernation. What confused me was the following paragraph on [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

"In reality, if you use hibernation you need what was outlined in the relevant paragraph above, otherwise you need as much swap space as your system will use - which actually may be very little in a modern hardware setup. The only downside to having more swap space than you will actually use is the disk space you will be reserving for it."

Then the server manual led me to believe that too much swap and the computer will use it whether it needs it or not. In other words, if I have 8 GB RAM and the system rarely uses over 3 GB, it will use the swap anyway just because it's there.

---

### Post by hawkmage on 2012-05-19
Yes, the use of hibernation will require as much swap as the amount of memory used so at swap should be at least the physical RAM size.  

Also allocating a lot more swap that you will ever need is a waste of disk resources but not enough can be cause applications or even the OS to crash so I usually error on the high side.

Linux will not gratuitously swap just because it is there.  I have a system running Ubuntu Server 12.04 that runs DNS, a small Apache/Tomcat site and a few other services.  It is on an old system with 2Gb of RAM and I gave it 2 GB of swap.  it is currently using no swap and it is set for the default swappiness of 60.

---

### Post by scottbomb on 2012-05-19
Excellent. Thank you all.

---

