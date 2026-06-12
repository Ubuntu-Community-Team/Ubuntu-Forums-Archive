---
title: "ubuntu 8.04 SW RAID1 - md0 is not clean"
date: 2010-03-16
forum: Server Platforms
---

### Post by turtlee on 2010-03-16
hello, can someone help me pls?
I tried build raid, at first time was all OK, status was ACTIVE,CLEAN.
Then i changed one of HDD. ( because it was crash) Than i rebuild this array, and status is only active.I dont know, what does it mean the "CLEAN"?
thanks for all ansfer

[SIZE=4]here is the code:[/SIZE]
[FONT=Arial Narrow]sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Feb 26 20:29:22 2010
     Raid Level : raid1
     Array Size : 76272704 (72.74 GiB 78.10 GB)
  Used Dev Size : 76272704 (72.74 GiB 78.10 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Mar 14 23:18:00 2010
          State : **active**
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 39186803:217b35f6:936da9ed:72cae159 (local to host freecomp)
         Events : 0.125860

    Number   Major   Minor   RaidDevice State
       0      22        1        0      active sync   /dev/hdc1
       1       3        1        1      active sync   /dev/hda1[/FONT]

---

