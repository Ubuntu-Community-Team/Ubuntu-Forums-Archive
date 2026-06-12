---
title: "Rebuild Raid 5"
date: 2015-07-21
forum: Server Platforms
---

### Post by joao7 on 2015-07-21
Hello

I have a RAID 4 with 4 HDD

one of my drives failed, and after that one of the drives changed to spare.

root@storage:/# mdadm -D /dev/md1
/dev/md1:
        Version : 01.00
  Creation Time : Wed Sep 10 18:54:47 2014
     Raid Level : raid5
     Array Size : 5854422528 (5583.21 GiB 5994.93 GB)
  Used Dev Size : 3902948352 (3722.14 GiB 3996.62 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent


    Update Time : Tue Jul  7 09:21:34 2015
          State : clean, degraded
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1


         Layout : left-symmetric
     Chunk Size : 64K


           Name : storage:1  (local to host storage)
           UUID : eb95f611:2296fbea:6f602af2:927375ea
         Events : 493154


    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       18        1      active sync   /dev/sdb2
       2       0        0        2      removed
       3       8       50        3      active sync   /dev/sdd2


       2       8       34        -      spare   /dev/sdc2
root@storage:/#


5


Personalities : [linear] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4]
md1 : active raid5 sdc2[2](S) sdd2[3] sdb2[1]
      5854422528 blocks super 1.0 level 5, 64k chunk, algorithm 2 [4/2] [_U_U]


md0 : active raid1 sdd1[3] sdc1[2] sdb1[1]
      2040128 blocks [4/3] [_UUU]


unused devices: <none>

There is any way to move the drive to the array again without loose the data ?

Thanks and Regards

---

