---
title: "Accidentally tried to install GRUB on Raid-5"
date: 2012-04-28
forum: Server Platforms
---

### Post by CheesyPuffs144 on 2012-04-28
I previously had 9.10 Desktop installed. I decided to install 12.04 Server today.

I have 7 hard drives, an 80GB where I keep the OS, and 6 750GBs that are in a RAID 5.

When installing 12.04 today, I **accidentally tried to install GRUB onto my first RAID disk**, which failed. I then installed it onto the 80GB hard drive, and then continued. First boot, I install mdadm, restart, and it tells me that I have a degraded drive.

Would attempting to install GRUB onto the RAID disk cause this? If so, can it be fixed?

```
$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sda1[0](S)
      732571904 blocks
       
md0 : active (auto-read-only) raid5 sdb[1] sdd[3] sdc[2] sdf[5] sde[4]
      3662872320 blocks level 5, 64k chunk, algorithm 2 [6/5] [_UUUUU]
      
unused devices: <none>
```

```
$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Wed Sep 29 12:58:49 2010
     Raid Level : raid5
     Array Size : 3662872320 (3493.19 GiB 3750.78 GB)
  Used Dev Size : 732574464 (698.64 GiB 750.16 GB)
   Raid Devices : 6
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Apr 28 17:54:23 2012
          State : clean, degraded 
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 0256470b:539bbed9:80414c21:2873e302 (local to host nemesis)
         Events : 0.20

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd
       4       8       64        4      active sync   /dev/sde
       5       8       80        5      active sync   /dev/sdf

```

---

