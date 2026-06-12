---
title: "Stupid Question"
date: 2007-12-25
forum: The Cafe
---

### Post by Fred_E _krugar on 2007-12-25
Can someone please explain to me what the difference between Linux distros with i386 and i686 which is better to use with Quad core CPUs and 2gig of ram???

---

### Post by EdThaSlayer on 2007-12-25
> **Fred_E _krugar said:**
> Can someone please explain to me what the difference between Linux distros with i386 and i686 which is better to use with Quad core CPUs and 2gig of ram???

According to Wikipedia i686 supports these processors:

> 
i686 Processors
_ Intel_
    * Pentium Pro
    * Pentium II
    * Pentium III
    * Pentium IV
    * Celeron
    * Pentium M
    * Xeon
    * Core
_AMD_
    * Athlon
    * Athlon XP
    * Duron
    * Sempron

I'm not sure about quad core cpus, but it should support dual-core intel processors. I prefer to download the i386 iso since I know it will work on almost any computer. :popcorn:

---

### Post by Fred_E _krugar on 2007-12-25
I did find out that the quads are considered i686 I will try the i686 version of FC8 seeing how thei686 is supposed to be more optimized for my set up, meaning running a little quicker I hope.

---

### Post by mindtrick on 2007-12-25
[http://distrowatch.com/search.php?category=Desktop&origin=All&basedon=All&desktop=All&architecture=i686&status=Active](http://distrowatch.com/search.php?category=Desktop&origin=All&basedon=All&desktop=All&architecture=i686&status=Active)

---

### Post by jeffus_il on 2007-12-25
In general Linux built with i386 will be compatible  with the ols 386 processor instructions, optimizations etc, and the i686 would be compatible  with  the latest processors.

The ubuntu  downloads  offer you:
1. Standard personal computer (x86 architecture, Pentium*TM*, Celeron*TM*, Athlon*TM*, Sempron*TM*)                 
2. 64bit AMD and Intel computers             
3. Sun UltraSPARC based


Choose the first which will give you support for SMP, afterwards just make sure that "uname -a" command gives you a kernel name ending in -generic and not -386, this will check that you have SMP support

---

### Post by LaRoza on 2007-12-25
> **Fred_E _krugar said:**
> Can someone please explain to me what the difference between Linux distros with i386 and i686 which is better to use with Quad core CPUs and 2gig of ram???

If you have a 64 bit processor, you should use a 64 bit OS, assuming everything else is equal.

---

### Post by Fred_E _krugar on 2007-12-25
Thanks guys for the replies, I would run the 64bit,but it is a pain with flash  and such .

---

### Post by overdrank on 2007-12-25
> **Fred_E _krugar said:**
> Thanks guys for the replies, I would run the 64bit,but it is a pain with flash  and such .

HI and the 64 bit is no pain! :KS
[http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)

---

### Post by Fred_E _krugar on 2007-12-25
Ok then will wine and games run alright??

---

### Post by overdrank on 2007-12-25
> **Fred_E _krugar said:**
> Ok then will wine and games run alright??

I have not used wine but this link may help
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

---

