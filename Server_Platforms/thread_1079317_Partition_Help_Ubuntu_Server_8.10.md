---
title: "Partition Help Ubuntu Server 8.10"
date: 2009-02-24
forum: Server Platforms
---

### Post by matey3 on 2009-02-24
Hello;
I have a 250 HDD and I want to install the server on it but whenever I choose to create partition manually, the server goes thru the routines (copy files from CD to some place??) and then reboots into Grub Error 22!?
I have to re-install from scratch over and over to no avail?

I want to have 3 partitions like;
1- for / (for files and directories)10GB
2- for swap, 2GB
3-Rest for LVM

But when I do this the server does not boot?
I want to have the following when I do an fdisk -l :
sda1 * / ext3 fs 83
sda2     swap    82
sda3     lvm     8e

not some thing like this (which I get when I go with auto partition from setup menu):
sdb1
sdc5
sda7
sdb2 * /
sdc3
and a lot of sda,b,c etc. etc...
looks ugly and disorganized.

 some one said that the reason for diff. partitions is that if one folder gets corrupted or deleted, we would not have to re-do the whole server ...which make sense, but why cant linux setup those directories under / instead of demanding diff. partitions?
or at least stop me before going thru the whole hour of routine?


Thanks for any help in advance;

---

### Post by freerkkalsbeek on 2009-02-24
Please describe in more detail what steps your going thru until the system reboots.

Upfront: 
If you re-partition your drive/re-use existing partitions make sure
1. you format the partitions and 
2. select on which mountpoint you want them

Regards,
Freerk

---

