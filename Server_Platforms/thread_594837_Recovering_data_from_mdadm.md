---
title: "Recovering data from mdadm"
date: 2007-10-28
forum: Server Platforms
---

### Post by galeron on 2007-10-28
Hi guys,

I had a RAID1 data partition on mdadm (system files are on another hard disk). My computer got wrecked. Long story short, only 1 hard disk is working now, and I've no OS. 

Is there any way to recover my data using a live CD of some sort?

Thanks!

---

### Post by koenn on 2007-10-28
it's gonna depend on what got wrecked and what is working. 
Never been there before, but i think it's theoretically possible to either
1/ mount the remaining disk and have access to the data, assuming that that 1 remaining disk is part of the mirror that contained the data
2/ install a new OS and try to move the raid to that system and rebuild it their, without loss of data. 

But, again, it all depends on what you had for disks to start with, and which of your disks are still working

---

