---
title: "Compiling Ubuntu from scratch 2"
date: 2010-01-29
forum: The Cafe
---

### Post by fahadysf on 2010-01-29
But would you get any benefit tuning for your processor type ('-march=core2 -mtune=core2 -msse4 etc etc' ?

---

### Post by cariboo on 2010-01-29
The above post was tacked on to the end of a 5 year old thread.

See the origional thread [here]("http://ubuntuforums.org/showthread.php?t=43096")

---

### Post by Xbehave on 2010-01-29
Not really, i doubt you will gain more than a few % and it will take agers to do, ofc the only way to know for sure is to do it and benchmark it.

I doubt it's too hard to do but it will take quite some time, i think youd need to look at apt-src or something like
```
apt-get build-dep $program;apt-get source -b $program
```
edit your default build options and script a way to do all of your apps then leave it running for a few hours.

---

### Post by dragos240 on 2010-01-29
> **cariboo907 said:**
> The above post was tacked on to the end of a 5 year old thread.

See the original thread [here]("http://ubuntuforums.org/showthread.php?t=43096")

Fixed.

---

### Post by cariboo on 2010-01-29
Thanks dragos240, I noticed it was spelled wrong, but didn't change it. :)

---

### Post by MaxIBoy on 2010-01-29
Believe it or not, you can get some benefit-- not significantly by compiling for your CPU architecture (although that certainly doesn't hurt,) but by stripping out unneeded drivers (smaller kernel that loads faster,) eliminating the initrd (also for faster boot time,) upping the tickrate (better desktop latency,) applying the BFS patch (much better performance,) and much more. There are plenty of knobs and switches which cause crashes on a minority of hardware and need to be disabled for everyone. 

Don't expect miracles, but the kernel you choose can clearly matter for performance:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)


On the other hand, if you really mean "compiling Ubuntu from scratch," you need to do a lot more than just the kernel.

---

### Post by Xbehave on 2010-01-29
> **MaxIBoy said:**
> Believe it or not, you can get some benefit-- not significantly by compiling for your CPU architecture (although that certainly doesn't hurt,) but by stripping out unneeded drivers (smaller kernel that loads faster,) eliminating the initrd (also for faster boot time,) upping the tickrate (better desktop latency,) applying the BFS patch (much better performance,) and much more. There are plenty of knobs and switches which cause crashes on a minority of hardware and need to be disabled for everyone. 
Most of that will only decrease boot time (a modular kernel + initrd + udev meands only needed drivers are loaded)
The BFS patch is debatable, I've seen claims it has little effect (but ofc the mainline devs would say that)
The tickrate you are right about though, default ubuntu=100, best for desktop=10000 (but it might cost you a tiny bit of battery life)

---

