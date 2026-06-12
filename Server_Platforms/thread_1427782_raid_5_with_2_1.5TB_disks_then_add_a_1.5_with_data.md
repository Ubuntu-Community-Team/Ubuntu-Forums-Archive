---
title: "raid 5 with 2 1.5TB disks then add a 1.5 with data?"
date: 2010-03-11
forum: Server Platforms
---

### Post by speed32219 on 2010-03-11
current setup is Karmic 2.6.31-14-server in older spare PC strictly home server for htpc (ISO's, WAV, Pictures and home videos).  I have 2 new-1.5TB drives that are not installed yet and another one that is installed with 900GB of data on it. 
 df -h
/dev/sdb1             1.4T  878G  429G  68% /media/disk-1  1.5TB
/dev/sdc1             459G  120G  317G  28% /media/disk-2  500GB
/dev/sdd1             925G  627G  251G  72% /media/disk-3  1TB

I have two new 1.5TB disks (1 WD WD15ARS and 1 Samsung F2 HD154UI)
After having a 1.5TB WD disk one month ago die on me plus a 320GB went out 2 months earlier I decided it was time for some form of protection.

Questions:
Can I install the two new 1.5TB disks as a degraded Raid5 with LVM, then copy the data from /dev/sdb1 (890GB) to the new degraded raid.  Then  just grow/add to the array the /dev/sdb1 (1.5TB that I just copied the data from) and redo the partition to raid5 + lvm?  

Or, install the 2 new 1.5TB drives and create two 700GB raid5 partitions with LVM per drive. Then copy the  data from /dev/sdb1 into the array and then set it up with two 700GB partitions w/LVM also,  then copy the data from the 1TB disk into the array?

Just wondering, because of the physical size of the HD, if it would be better to have multiple partitions per drive.

---

### Post by Ellhound on 2010-03-12
Option 1 will work just fine. Create a degraded array with the new disks, copy data to it, and then add the third disk.

---

### Post by speed32219 on 2010-03-12
Thanks, that's what I'll do. 

Just wanted to be sure, it gets a little confusing reading all this stuff.

---

### Post by cascade9 on 2010-03-12
Mixing and matching HDDs for a RAID array is possible, but never reccomeneded. If your WD drive is a EARS (which I assume it is, they come in EARS and EADS versions now) I'd be extra carefull and double-check before even trying this with it . WD EARS use 4K sectors not 512B. Using an unaligned EARS drive can give a major performance drop. On a RAID system this could affect the whole array. I dont know how RAID will deal with drives of different sector sizes....you could have major issues.

---

