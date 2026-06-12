---
title: "The multiple core myth ?"
date: 2010-04-14
forum: The Cafe
---

### Post by user1397 on 2010-04-14
I read somewhere (can't remember right now) that phrase: the multiple core myth, referencing having multi-core processors and how it was some sort of marketing scheme to fool the public into thinking the more cores the faster your computer is.

Now, I know very little on this subject, so I am seeking some enlightenment (No, no pun intended you e17 users)

Since Moore's law states chips can only get so much smaller, and that minimum chip size will be reached in the next decade or two, what's to stop us from just having multi-core processors as a solution to Moore's law?

---

### Post by zekopeko on 2010-04-14
> **ubuntuman001 said:**
> I read somewhere (can't remember right now) that phrase: the multiple core myth, referencing having multi-core processors and how it was some sort of marketing scheme to fool the public into thinking the more cores the faster your computer is.

Now, I know very little on this subject, so I am seeking some enlightenment (No, no pun intended you e17 users)

Since Moore's law states chips can only get so much smaller, and that minimum size will be reach in the next decade or two, what's to stop us from just having multi-core processors as a solution to Moore's law?

You did notice that processors have stopped going the Ghz route a few years ago? 

There is no myth there. If an application is written to take advantage of multi-core processors it will be faster.

Multi-core CPUs are the future.

---

### Post by Paqman on 2010-04-14
> **ubuntuman001 said:**
> 
Now, I know very little on this subject, so I am seeking some enlightenment (No, no pun intended you e17 users)


The problem is one of perception. The marketting suggests that having two 3GHz cores makes your machine faster than having one 3.1GHz core.

And it will, for *some* tasks. And for other tasks, the single core 3.1GHz machine will win.

The issue is how the software uses the fact that it has two routes through the processor, and is (appropriately) twofold:
[LIST=1]
[*]Some tasks either can't be split up into seperate threads, or don't benefit from it.
[*]Generally speaking, although operating systems have been written to be highly multi-threaded for a while, apps aren't. If your app is single-threaded, it will only ever use one core.
[/LIST]

In both the above cases, it doesn't matter how many cores you have, only clock speed. So a fast single core machine will outperform a multi-core one clocked at a lower speed (disregarding for the moment buses, memory, etc)

The bottom line is that a dual-core CPU can't actually be guaranteed to be any faster than a single-core one, although in real-world computing situations they are likely to show a decent improvement if you average out a wide range of tasks.

---

### Post by cascade9 on 2010-04-14
> **Paqman said:**
> The problem is one of perception. The marketting suggests that having two 3GHz cores makes your machine faster than having one 3.1GHz core.

And it will, for *some* tasks. And for other tasks, the single core 3.1GHz machine will win.

The issue is how the software uses the fact that it has two routes through the processor, and is (appropriately) twofold:
[LIST=1]
[*]Some tasks either can't be split up into seperate threads, or don't benefit from it.
[*]Generally speaking, although operating systems have been written to be highly multi-threaded for a while, apps aren't. If your app is single-threaded, it will only ever use one core.
[/LIST]

In both the above cases, it doesn't matter how many cores you have, only clock speed. So a fast single core machine will outperform a multi-core one clocked at a lower speed (disregarding for the moment buses, memory, etc)

The bottom line is that a dual-core CPU can't actually be guaranteed to be any faster than a single-core one, although in real-world computing situations they are likely to show a decent improvement if you average out a wide range of tasks.

I pretty much agree, barring one point- its not just clock speed. Cache matters, a lot. If it didnt a XGhz celeron would be as fast as a XGhz P4, etc. On single threaded programs (and multi-threaded for that matter), a CPU with more cache and less Ghz can be faster than a CPU with less cache and more Ghz.

---

### Post by tom66 on 2010-04-14
And not just cache. Architecture as well. Pipelining, FLOPS, 32- or 64-bit etc.

---

### Post by Paqman on 2010-04-14
> **cascade9 said:**
> I pretty much agree, barring one point- its not just clock speed. Cache matters, a lot.

That would be one of the "etc" parts of:
> (disregarding for the moment buses, memory, etc)

---

### Post by tica vun on 2010-04-14
> **ubuntuman001 said:**
> Since Moore's law states chips can only get so much smaller, and that minimum size will be reach in the next decade or two, what's to stop us from just having multi-core processors as a solution to Moore's law?

That's not what Moore's law says. Moore's law says that when the limits of current technology are achieved (actually, well before that happens), a new, more efficient one will come along. This has been the case for centuries and there's no reason why we couldn't move on from the present computing paradigm (integrated circuits).

---

### Post by doas777 on 2010-04-14
really the big differance is in your apps threading model.
a cpu/core can run exactly one thread at a time, so if you have a single threaded application it will use at most 1 core. to optimize that, you need a chip with a faster frequency (GHz) to run the thread faster.

a multi threaded app can run each of it;s threads on a seperate core/cpu though, so for a app that is "evenly" multithreaded you can run it much faster on a multicore than on a single core. other apps will use extra threads but only to perform certain tasks (IO/loading data from disk to ram is one common one), so they won't really be sped up by installing a multicore, except when doing one of those multithreaded tasks.

multithreading is often much more complicated than single thread programming, so often many developers will go the safe route of writing a slower simpler app than faster one that uses multiple cores, but has intermittent and hard-to-reproduce concurrency or thread access bugs in it. 

hth

---

### Post by Half-Left on 2010-04-14
> **Paqman said:**
> Yeah, but the OP wasn't really asking about what defined CPU performance overall, just what effect adding extra cores had.

Which is what he said, "architecture". You can have as many cores as you want but if it's architecture is is poor, it will be slow.

If you want an example of this, look at the Pentium 4s architecture . Although it's only one CPU, Intel had to ramp up the Mhz to getting performing good. Thankfully, Intel's newer dual core architecture is a lot more efficient, making better use of the cores at lower clock speeds.

The trick is to make your architecture work best at lower clock speeds, avoiding heat issues.

---

### Post by Paqman on 2010-04-14
> **Half-Left said:**
> 
The trick is to make your architecture work best at lower clock speeds, avoiding heat issues.

Ah, but if you ask the marketing people, the trick is to have a bigger number on the box than the last generation you were trying to sell ;)

---

### Post by doas777 on 2010-04-14
> **tica vun said:**
> That's not what Moore's law says. Moore's law says that when the limits of current technology are achieved (actually, well before that happens), a new, more efficient one will come along. This has been the case for centuries and there's no reason why we couldn't move on from the present computing paradigm (integrated circuits).
the problem with moores curves, is the power wall. once we got to about 3ghz, we cou;dn't go any further without adding more power, but that adds heat which increases error rate, reduces lifespan, and makes cost of ownership higher (especially for data center admins).

now that we are combining 25-40nm manufacturing tech and reduced power componenets, we are finally starting to see the 3.2ghz wall crumble, but since a slow multicore suits most home users multitasking pursuits better than a 1000USD 4.1ghz single core chip, there just isn't as much incentive to bring them to market.  
besides, nowadays the "I know just enough to be dangerous" crowd is focused on diskspace and ram (since they remember all the vista problems over the last few years that are fixed by throwing ram at the problem), so the comparatively complex CPU just gets less billing. that may be one of the reasons they are pushing multicore chips: "2 cores instead of 1" is much easier to explain than Caches, FSB speed, clock, or even what a hz really is.

btw moores law is somewhat more specific than the theoretical generic evolution of technology. 
check this out: [http://en.wikipedia.org/wiki/Moore%27s_law](http://en.wikipedia.org/wiki/Moore%27s_law)

---

### Post by Meep3D on 2010-04-14
> **tica vun said:**
> That's not what Moore's law says. Moore's law says that when the limits of current technology are achieved (actually, well before that happens), a new, more efficient one will come along. This has been the case for centuries and there's no reason why we couldn't move on from the present computing paradigm (integrated circuits).

I thought it was just the fact that the number of transistors that can be fit onto a standard chip will double every two years.

---

### Post by moster on 2010-04-14
Ubuntuman, there is no completely right or wrong here.

If you open this interesting thread  below that are going for years now, you will see that 1 core 3,0 GHz intel few years back is double slower then 3,0 GHz intel now. And testing only 1 core.

[http://ubuntuforums.org/showthread.php?t=60264&highlight=superpi]("http://ubuntuforums.org/showthread.php?t=60264&highlight=superpi")

---

### Post by Half-Left on 2010-04-14
> **Paqman said:**
> Ah, but if you ask the marketing people, the trick is to have a bigger number on the box than the last generation you were trying to sell ;)

haha, well yes, marketing is king when people don't know about underlying information but that's another myth in the "mhz myth".

---

### Post by swoll1980 on 2010-04-14
> **zekopeko said:**
> 

Multi-core CPUs are the future.
[Diamond transistors]("http://www.geek.com/articles/chips/81ghz-diamond-semiconductor-created-20030827/") are the future.

---

### Post by blur xc on 2010-04-14
I've wondered this- what if you had 4 single threaded apps running at the same time on a single core vs. a quadcore cpu?  Does the OS split each process up to run on each core, or will all four apps try to hog up the same core of the quad core cpu?

Also- it's been my observation (I've got my conky setup to show my cpu usage on my desktop so I watch it all the time when doing cpu intensive tasks) that most applications that need lots of cpu are coded to run multi threaded.  Kdenlive, Handbrake, Bibble, etc.., all run multi threaded.  In any of those programs, one process might time 30minutes to and hour to complete.  Stupid simple things that get done in under 5 seconds regardless of number of cores used, who cares...  It's only 5 seconds.  I'm not impatient to the point of being irritated that it's taking 2 seconds longer to do by not being multi threaded.

All that said- I'm hunting for a good deal on a good quad core upgrade...  

BM

---

### Post by Paqman on 2010-04-14
> **Meep3D said:**
> I thought it was just the fact that the number of transistors that can be fit onto a standard chip will double every two years.

Yep, and crucially: all for the same price.

> **blur xc said:**
> I've wondered this- what if you had 4 single threaded apps running at the same time on a single core vs. a quadcore cpu?  Does the OS split each process up to run on each core,

Yes, it's called SMP, and every OS has been able to do it for years. You'll actually find that even if you only run a single app, the OS will swap it back and forth between cores. 

Having tons of cores is great for multitasking. To be honest, since so few apps are good at multithreading, the fact that OSes do this is the real reason multi-core machines are better for end users.

---

### Post by swoll1980 on 2010-04-14
It's great for VMs too. They can be assigned any number of cores as their own.

---

### Post by user1397 on 2010-04-14
Thanks for all the responses everyone, yall enlighten'd me. :)

---

### Post by doas777 on 2010-04-14
> **blur xc said:**
> I've wondered this- what if you had 4 single threaded apps running at the same time on a single core vs. a quadcore cpu?  Does the OS split each process up to run on each core, or will all four apps try to hog up the same core of the quad core cpu?

Also- it's been my observation (I've got my conky setup to show my cpu usage on my desktop so I watch it all the time when doing cpu intensive tasks) that most applications that need lots of cpu are coded to run multi threaded.  Kdenlive, Handbrake, Bibble, etc.., all run multi threaded.  In any of those programs, one process might time 30minutes to and hour to complete.  Stupid simple things that get done in under 5 seconds regardless of number of cores used, who cares...  It's only 5 seconds.  I'm not impatient to the point of being irritated that it's taking 2 seconds longer to do by not being multi threaded.

All that said- I'm hunting for a good deal on a good quad core upgrade...  

BM

in theory, I believe the kernel wouid run the multithread on different cores based on it's scheduling paradigm. of course if those cores were already in use, it would just timeswap the threads the same way the single core would handle it. it's still timeslice multiplexing, but instead of watching 1 CPU, it watches 4, and runs whatever needs run wherever it can be.

---

### Post by blur xc on 2010-04-14
> **doas777 said:**
> in theory, I believe the kernel wouid run the multithread on different cores based on it's scheduling paradigm. of course if those cores were already in use, it would just timeswap the threads the same way the single core would handle it. it's still timeslice multiplexing, but instead of watching 1 CPU, it watches 4, and runs whatever needs run wherever it can be.

So, it stands to reason that even if you only every use single threaded apps, but are multitasking, then a multicore cpu will be faster than a single core cpu (all esle being equal).

BM

---

### Post by doas777 on 2010-04-14
> **blur xc said:**
> So, it stands to reason that even if you only every use single threaded apps, but are multitasking, then a multicore cpu will be faster than a single core cpu (all esle being equal).

BM

correct, though there is a balancing effect if the threads are all short lived.

---

### Post by zeez on 2010-04-14
> **Paqman said:**
> The problem is one of perception. The marketting suggests that having two 3GHz cores makes your machine faster than having one 3.1GHz core.

And it will, for *some* tasks. And for other tasks, the single core 3.1GHz machine will win.

The issue is how the software uses the fact that it has two routes through the processor, and is (appropriately) twofold:
[LIST=1]
[*]Some tasks either can't be split up into seperate threads, or don't benefit from it.
[*]Generally speaking, although operating systems have been written to be highly multi-threaded for a while, apps aren't. If your app is single-threaded, it will only ever use one core.
[/LIST]

In both the above cases, it doesn't matter how many cores you have, only clock speed. So a fast single core machine will outperform a multi-core one clocked at a lower speed (disregarding for the moment buses, memory, etc)

The bottom line is that a dual-core CPU can't actually be guaranteed to be any faster than a single-core one, although in real-world computing situations they are likely to show a decent improvement if you average out a wide range of tasks.

indeed, to enchant this response i would refer to [Amdahl's Law]("http://en.wikipedia.org/wiki/Amdahl%27s_law")

---

### Post by handy on 2010-04-14
> **blur xc said:**
> So, it stands to reason that even if you only every use single threaded apps, but are multitasking, then a multicore cpu will be faster than a single core cpu (all esle being equal).

BM

I generally think of it in the simple fashion that multi-core CPUs offer better results for people that multitask a lot.

The next time I build myself a machine I'll go for a quad-core, as I do multitask a lot. (Well my machine does, I'm personally terrible at it these days. ;))

---

### Post by MasterNetra on 2010-04-14
> **swoll1980 said:**
> [Diamond transistors]("http://www.geek.com/articles/chips/81ghz-diamond-semiconductor-created-20030827/") are the future.

I disagree, [[COLOR="Blue"]memristors[/COLOR]]("http://www.memristor.org/") are the future. Although those most likely will precede the memristor and might even be used with it in some fashion.

---

### Post by the yawner on 2010-04-15
> **MasterNetra said:**
> I disagree, [[COLOR="Blue"]memristors[/COLOR]]("http://www.memristor.org/") are the future. Although those most likely will precede the memristor and might even be used with it in some fashion.

This.

I'm actually excited with this development.

---

### Post by blueshiftoverwatch on 2010-04-15
If x86 based architectures didn't have a near monopoly on the consumer end computing market and we had competition in the form of PowerPC, ARM, MIPS, and possibly even new and exciting technologies that don't even exist yet. Would multicored CPU's be hitting the market yet?

I've heard that the only reason why Intel and AMD are trying to put as many cores on a die as possible is because there are so many problems with x86 (it's been around since the 70's) that it's easier to just keep adding more cores than it is to switch to another architecture or design a better one. Mostly because of software compatibility issues.

---

