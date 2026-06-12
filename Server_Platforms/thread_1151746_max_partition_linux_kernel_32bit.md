---
title: "max partition linux kernel 32bit"
date: 2009-05-07
forum: Server Platforms
---

### Post by DJJo on 2009-05-07
i got a Ubuntu server with LVM on it and a XFS partition.

with LVM i made a Partition from 500GB + 1TB.
but i want to bilt a partition form 1TB 

I would like to do a hard drive of 1TB behind it.

is this possible. becase i got a 32bit server. and i read somewhere that the max Partition size is 2TB

I also got oder disk from 250GB + 8 GB + 10 GB
Ubuntu server 8.04.1
LVM version 2.02.26 
Linux 2.6.24-21-server on i686

i hope i make may self clear

---

### Post by Vegan on 2009-05-07
I simply erased my disk and let the distro partition it as it wanted. The 2 TB limit is the MBR limit for booting a disk on most machines. Its just one of a staggering number of limitations that have plaugued the computer business for decades.

---

### Post by DJJo on 2009-05-07
> **Vegan said:**
> I simply erased my disk and let the distro partition it as it wanted. The 2 TB limit is the MBR limit for booting a disk on most machines. Its just one of a staggering number of limitations that have plaugued the computer business for decades.
The lager partiiton is not my boot disk.
the ubuntu server is runing on the 10G and the 8G disk

---

### Post by DJJo on 2009-05-08
I think i Found it.

[http://www.walkernews.net/2007/07/02/maximum-size-of-a-logical-volume-in-lvm/](http://www.walkernews.net/2007/07/02/maximum-size-of-a-logical-volume-in-lvm/)

> 
[LIST]
[*]Linux kernel version 2.4.x limit the maximum LV size to 2TB.
[*]Some older Linux kernel prior to 2.4.x, the maximum LV size is limited to 1TB (caused by the integer signedness problems in the block layer).
[*]The combination of 32-bit CPU and Linux kernel version 2.6.x, the limit of logical volume size is maximized at 16TB.
[*]For Linux kernel 2.6.x running on 64-bit CPU, the maximum LV size is 8EB (extremely terrible big storage for this time being!)
[/LIST]


So it sould be 16 TB.

---

