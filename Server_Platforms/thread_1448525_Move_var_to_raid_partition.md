---
title: "Move /var to raid partition"
date: 2010-04-06
forum: Server Platforms
---

### Post by seangee on 2010-04-06
I'm in the process of setting up a home server. I have had a play with FREENAS but had some serious issues with the embedded version so I am replicating all the features  I need (plus a few :)) using 9.10 server. 

The PC I'm using has 4 1Tb SATA disks configured in RAID 5 (1 spare) using MDADM. I am booting off a USB stick. So far everything is working really well but once I have completed the system I would like to mount the USB drive as readonly or at very least not write to it.

Will I run into any problems if I move /var onto the RAID disk? I guess my biggest concern is that the system will try to access this before the RAID disk is mounted. If this is possible is there anything else, besides swap, I should / could move?

---

### Post by richardjh on 2010-04-06
Disks will be mounted before services start and /var gets written to.

There are some directories such as /bin /etc and /dev that cannot be on seperate partitions but it is quite common to use another partition for /var.

---

