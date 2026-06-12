---
title: "Accessing Windows Partition from VM Ubuntu"
date: 2010-09-18
forum: Virtualisation
---

### Post by GlenGrail on 2010-09-18
I have recently installed Ubuntu 10.04 on a virtual machine in Windows Vista, using Microsoft's Virtual PC. The installation seems to run fine. Is it possible, from inside the virtual Ubuntu, to access, say, the partition on my real hard drive on which Vista is installed? Or the partition which contains a real Linux installation? Or an external hard drive?

I have had some difficulty conceptualizing this problem for a Google search, and my attempts have yielded little. More broadly, I am asking whether the virtual machine is confined to itself, or whether it is able to reach out and manipulate other partitions, files lying outside the specific vhd on which it is installed. Likewise, is it possible to access files written on the vhd from outside the virtual machine?

A solution to either question--going from virtual to real or real to virtual--would solve my problem, I think. Thanks.

---

### Post by ilovelinux33467 on 2010-09-19
VirtualBox has this feature. It is called shared folders

---

### Post by GlenGrail on 2010-09-19
Excellent; thank you. I should have known to investigate alternatives before employing a Microsoft solution.

Unless I am mistaken, the post immediately above is an attempt to sell me underwear. And belts. Which sounds more like an Apple solution, in a Garden of Eden kind of way.

---

