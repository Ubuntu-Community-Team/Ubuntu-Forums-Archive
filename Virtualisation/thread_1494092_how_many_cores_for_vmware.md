---
title: "how many cores for vmware?"
date: 2010-05-26
forum: Virtualisation
---

### Post by mcbenz on 2010-05-26
I am considering to buy a computer to run Ubuntu host and windows guest.
My main use is to watch ppstream and youtube video, but they are so slow in my windows7 guest and basically not viewable in ubuntu.
My current system is
AMD Athlon 64x2 5000 
4GB DDR2-800 ram

I am considering a new motherboard and one of these AM3 processors:
Phenom II x6 1055T (2.8ghz) around CDN$220
Athlon II x4 635 (2.9ghz) around CDN$120
Phenom II x2 555 (3.1ghz) around CDN$104
Athlon II x3 435 (2.9ghz) around CDN$82

The questions are:
Is vmware single threaded or multithreaded? if so, is it threaded beyond two cores?
Does L3 cache matter for vmware?
Should I even consider 6 core?
Shoudl I switch to Intel?

---

### Post by fjgaude on 2010-05-28
I only use one... it seems to work best that way.

---

### Post by dcstar on 2010-05-29
If your host is not using the CPU much then multi-cpu seems to work ok in the VMs, however if your host is a heavy CPU user then one CPU works much better.

---

