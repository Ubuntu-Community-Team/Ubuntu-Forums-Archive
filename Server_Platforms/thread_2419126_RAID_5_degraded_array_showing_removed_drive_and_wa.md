---
title: "RAID 5 degraded array showing removed drive and want to add new drive to replace"
date: 2019-05-16
forum: Server Platforms
---

### Post by mtader2 on 2019-05-16
I had an issue with a drive showing as removed, so I checked the cables, etc, and when I restarted, I now have an entry that shows a drive as removed, and the one I reconnected as "spare".  How do I get rid of the "removed" and make the spare the active one?

~$ sudo mdadm --detail /dev/md127

/dev/md127:
        Version : 1.2
  Creation Time : Thu Feb  2 02:08:29 2017
     Raid Level : raid5
     Array Size : 14650917888 (13972.20 GiB 15002.54 GB)
  Used Dev Size : 4883639296 (4657.40 GiB 5000.85 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Thu May 16 22:22:44 2019
          State : clean, degraded 
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

  Delta Devices : 1, (4->5)

          

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd
       2       8       64        2      active sync   /dev/sde
       4       8       80        3      active sync   /dev/sdf
       4       0        0        4      removed

       5       8       96        -      spare   /dev/sdg


~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : active raid5 sdg[5](S) sde[2] sdf[4] sdd[1] sdc[0]
      14650917888 blocks super 1.2 level 5, 512k chunk, algorithm 2 [5/4] [UUUU_]
      
md0 : active raid1 sdb1[2] sda1[1]
      100441984 blocks super 1.2 [2/2] [UU]
      
md1 : active raid1 sda5[1] sdb5[2]
      16702336 blocks super 1.2 [2/2] [UU]

---

### Post by TheFu on 2019-05-17
Did you try to add it back?

```
sudo mdadm /dev/md127 -a /dev/sdg
```
be certain to check the command options. I didn't look THAT close.

BTW, I'm not a fan of building arrays without having a partition table and 1 partition on each device. Reasons.

If the array refuses, there are some other things we can try.
5TB is an odd size. On a busy array, I've seen this take over a week to resync. If you can handle faster sync at the cost of slower RAID performance, there are some kernel settings to increase that disk throughput.

---

### Post by mtader2 on 2019-05-19
Cannot open /dev/sdg: Device or resource busy

---

### Post by mtader2 on 2019-06-04
Any ideas?

---

### Post by mtader2 on 2019-06-08
SOLVED...


sudo mdadm --assemble --run --force --update=resync /dev/md127 /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg

[SIZE=6]_**Took it from :**_[/SIZE]

Version : 1.2
  Creation Time : Thu Feb  2 02:08:29 2017
     Raid Level : raid5
     Array Size : 14650917888 (13972.20 GiB 15002.54 GB)
  Used Dev Size : 4883639296 (4657.40 GiB 5000.85 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Tue Jun  4 22:26:22 2019
          State : clean, degraded 
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

  Delta Devices : 1, (4->5)

           Name : Mediaserver:3  (local to host Mediaserver)
           UUID : 59b7651a:540e9ffa:5b30d0e5:d28c3356
         Events : 1226967

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd
       2       8       64        2      active sync   /dev/sde
       4       8       80        3      active sync   /dev/sdf
       4       0        0        4      removed

       5       8       96        -      spare   /dev/sdg


[SIZE=6]*_**To:**_*[/SIZE]


/dev/md127:
        Version : 1.2
  Creation Time : Thu Feb  2 02:08:29 2017
     Raid Level : raid5
     Array Size : 19534557184 (18629.61 GiB 20003.39 GB)
  Used Dev Size : 4883639296 (4657.40 GiB 5000.85 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Sat Jun  8 09:48:11 2019
          State : clean 
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : Mediaserver:3  (local to host Mediaserver)
           UUID : 59b7651a:540e9ffa:5b30d0e5:d28c3356
         Events : 1358798

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd
       2       8       64        2      active sync   /dev/sde
       4       8       80        3      active sync   /dev/sdf
       5       8       96        4      active sync   /dev/sdg

---

