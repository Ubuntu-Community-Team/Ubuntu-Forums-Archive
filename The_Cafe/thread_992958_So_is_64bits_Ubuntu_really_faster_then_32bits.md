---
title: "So is 64bits Ubuntu really faster then 32bits?"
date: 2008-11-25
forum: The Cafe
---

### Post by _sAm_ on 2008-11-25
My pc have an Intel 2 Duo E6850 CPU, and 4gigs with ram(DDR2 8500), and 512mb ram on the gpu. I have Vista sp1 32bits and Ubuntu 8.10 64bits installed(dual-boot).

I wanted to see if there is any different in speed between them, and installed Handbrake on both(the 64bits version on Ubuntu). The simple test was to take a small film(*.ISO file with the size 198mb), and convert it to MKV, and take the time with a stopwatch.

Before watching on the times, witch one do you think was the fastest? 























Times;
Handbrake on Vista;  7.28 min.
Handbrake on Ubuntu: 7.29 min. 

The output file(*.MKV) had the same size on both. I tried once more in Ubuntu and htop showed both cores in use(mostly on 99%).

Comments?

---

### Post by Paqman on 2008-11-25
> **_sAm_ said:**
> 
Comments?

All you've really tested is how fast one app works on two different OSes. 32/64 bit is only one of many, many factors that would affect your outcome.

---

### Post by jomiolto on 2008-11-25
> **Paqman said:**
> All you've really tested is how fast one app works on two different OSes. 32/64 bit is only one of many, many factors that would affect your outcome.

Indeed. To get more accurate results you should try on 32-bit Ubuntu and 64-bit Ubuntu. Also, I'm not familiar with Handbrake, but it is possible that it makes no use of 64-bit arithmetics, which would make it just as fast on 32-bits and 64-bits.

For programs that make heavy use of 64-bit arithmetics the difference between a 32-bit version and 64-bit version can be huge. See [http://gmplib.org/32vs64.html]("http://gmplib.org/32vs64.html") for an example. Of course, on regular desktop usage there will be little difference between 32-bits and 64-bits, because most software don't make use of 64-bits yet...

HTH. :)

---

### Post by insane_alien on 2008-11-25
if there is 64-bit operations involved then 64-bit will be MUCH faster.

i have seen one program(it was to run some simulations) that went around 8 times as fast. although i am sure a lot of that benefit was from the 8GB of RAM.

---

### Post by Paqman on 2008-11-25
> **jomiolto said:**
> Of course, on regular desktop usage there will be little difference between 32-bits and 64-bits, because most software don't make use of 64-bits yet...


That would be my anecdotal take on it. Overall performance is not much different, except for some apps (eg: Gimp) where there is a definite speed boost.

It's a bit like the whole dual-core thing. Some apps are optimised for it, and some tasks are suited to it, but some just aren't and will run at exactly the same speed on a dual-core chip as they do on a single core of similar clock speed.

---

### Post by Therion on 2008-11-25
Having used both 32-bit and 64-bit distros pretty extensively, I can't say that I find 64-bit "faster" in the conventional sense.  Maybe for some things, but in the day-to-day world of personal computing I can't say I've noticed a difference in flat out, raw *speed*.  And if the difference requires a stopwatch to discern, for me, that's no difference.  I'm not interested in shaving fractions of a second off some synthetic benchmark.  Shave a few seconds off my startup time and then come talk to me.  That's just kinda where I'm coming from regarding the whole "faster" thing.

The advantage I do experience when using a 64-bit distro is more subjective, but nonetheless very real, in my experience.  64-bit distros offer a *smoother overall computing experience*.  I can't quite define what that is, not exactly, but you know when you feel it.  Normally when I've been running a 64-bit distro and then switch over to a 32-bit distro for whatever reason.  Much like the old saying about the difference between a Chevy and Cadillac, the difference is in the ride.  

All I can say is that having tried 64-bit computing on my system (Intel C2D E8500, 2GB of 1066Mhz DDR2, nVidia 8800GTS, 10K SATA Raptor HDD) I'll never go back to a 32-bit distro.  

Of course YMMV...




/two-cents worth

---

### Post by Cracauer on 2008-11-25
Apart from the obvious reasons why 64 bit machine code can be faster there's also a big reason why it can be slower: pointers are twice the size. 

Complicated code that makes use of a lot of pointers (e.g. in linked lists or graphs) will see an increase in total data size shuffled around, with the usual consequences of cache trashing, paging, TLA misses and subsequent software page table lookup etc etc. This is very real. Doesn't apply to most simple programs but can slow down complex programs noticeably.

---

### Post by Vadi on 2008-11-25
It depends on the CPU used too and the coding.

All in all, if you don't have a reason to stay away from 64bit, use it.

---

