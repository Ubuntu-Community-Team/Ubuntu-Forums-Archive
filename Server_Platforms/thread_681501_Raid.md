---
title: "Raid"
date: 2008-01-29
forum: Server Platforms
---

### Post by tresrob on 2008-01-29
I have installed a ubutnu server 7.10 

I make raid with 3 disk sata 500 gb 

I created md0 -- > sda1 sdb1 and sdc1 as spare
and md1 -- > sda2 sdb2 and sdc2 ad spare

in my mdadm.conf i have:

ARRAY /dev/md0 level= raid1 num=devices=2 UUID=***** spares=1
ARRAY /dev/md1 level= raid1 num=devices=2 UUID= ****  spares=1

Now i receive this message for md0 and md1:

This is an automatically generated mail message from mdadm
running on server***

A SparesMissing event had been detected on md device /dev/md1.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda2[0] sdb2[1]
      9767424 blocks [2/2] [UU]
      
md0 : active raid1 sda1[0] sdb1[1]
      478616384 blocks [2/2] [UU]
      
unused devices: <none>

how i can solve it

Many thanks 

Roberto

---

### Post by kyriakos1977 on 2008-02-14
wired configuration! 

does /dev/sdc2  exist in /proc/partitions?

Please Post 
mdadm -D /dev/md1

---

