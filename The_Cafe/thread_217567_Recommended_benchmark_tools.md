---
title: "Recommended benchmark tools?"
date: 2006-07-17
forum: The Cafe
---

### Post by halfvolle melk on 2006-07-17
Hi,
At the moment I'm running a 32bit Kubuntu but I'm planning on switching to the 64bit version. Before the switch I'd like to do some benchmarking and then offcourse repeat them after the switch. Problem is that I don't know a lot about benchmarking.

What tools to use to create meaningfull benchmarks? Should the tools themselves be recompiled for 64bit or should the identical 32bit version be used as to not get skewed results? Any pointers or addition remarks?
Thanks

---

### Post by mcduck on 2006-07-17
SuperPi is pretty much the standard for overclockers and other enthusiasts, and there's Linux version too. (Altough some people say that you can't compare windows version and linux version results. :rolleyes: )

Download it, extract somewhere and run from terminal. './pi 20' will calculate 1048576 decimal digits,and the usual test is done with './pi 23 for 8 million decimal digits (8M, 2^23).

[ftp://pi.super-computing.org/Linux/super_pi.tar.gz]("ftp://pi.super-computing.org/Linux/super_pi.tar.gz")

This is pure CPU/Memory top performance test, and has little to do with normal desktop computer usage. But it gives comparable results for performance.

(I just tried and got 8 min 27 sec for 8M test while running Gnome, XGL, firefox, mpd & some terminals, with AthlonXP@2,3GHz and 1GB RAM)

---

### Post by jinx099 on 2006-07-17
what about hard drive benching?

---

### Post by halfvolle melk on 2006-07-17
mcduck, thanks for your input, I'll check it out.

jinx099, [Bonnie](http://www.textuality.com/bonnie/) is supposed to do that.

I've read [this](http://tldp.org/HOWTO/Benchmarking-HOWTO.html), [this](http://linuxgazette.net/issue22/bench.html) and [this](http://lbs.sourceforge.net/) but I'm still not exactly sure how to properly do this. I think I'll just start and see what happens.

---

