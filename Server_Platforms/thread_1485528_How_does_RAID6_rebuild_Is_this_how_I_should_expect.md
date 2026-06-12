---
title: "How does RAID6 rebuild? Is this how I should expect it to resync?"
date: 2010-05-16
forum: Server Platforms
---

### Post by gjarboni on 2010-05-16
Hello,

Okay, I have a 12 disk raid 6 Array with 2 additional spare drives. Two of the drives got out of sync (because I was fat fingering the mdadm commands while trying to reassemble the array), so I added them back as spares. This is what mdadm is showing me:

```

root@tosh:# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Mon May  3 20:12:01 2010
     Raid Level : raid6
     Array Size : 1433719680 (1367.30 GiB 1468.13 GB)
  Used Dev Size : 143371968 (136.73 GiB 146.81 GB)
   Raid Devices : 12
  Total Devices : 14
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun May 16 22:55:27 2010
          State : clean, degraded, recovering
 Active Devices : 10
Working Devices : 14
 Failed Devices : 0
  Spare Devices : 4

     Chunk Size : 64K

 Rebuild Status : 1% complete

           UUID : 85c2ac23:e4ca497a:2d04beeb:169732b3
         Events : 0.22

    Number   Major   Minor   RaidDevice State
      15       8      209        0      spare rebuilding   /dev/sdn1
       1       0        0        1      removed
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1
       5       8       81        5      active sync   /dev/sdf1
       6       8       97        6      active sync   /dev/sdg1
       7       8      113        7      active sync   /dev/sdh1
       8       8      129        8      active sync   /dev/sdi1
       9       8      145        9      active sync   /dev/sdj1
      10       8      161       10      active sync   /dev/sdk1
      11       8      177       11      active sync   /dev/sdl1

      12       8      193        -      spare   /dev/sdm1
      13       8       17        -      spare   /dev/sdb1
      14       8        1        -      spare   /dev/sda1


```
Is this correct? Will Linux grab /dev/sdm1 (or /dev/sda1 or /dev/sdb1) and add it to the array when rebuilding with /dev/sdn1 is complete? Or is there some other command necessary to make that happen? Thanks for the help. The hardware is Fibre Channel private loop.

---

### Post by gjarboni on 2010-05-17
> **gjarboni said:**
> Will Linux grab /dev/sdm1 (or /dev/sda1 or /dev/sdb1) and add it to the array when rebuilding with /dev/sdn1 is complete?
In case someone else has the same question, the short answer is yes, the server grabbed /dev/sdm1 and is resyncing it right now.

Now I have another question. The whole reason for this mess was that the server didn't automatically configure the array on boot up. Now I've read up on mdadm.conf and have it set up correctly, so that shouldn't be a problem in the future. However, I'm curious why the array wasn't automatically assembled. (I know I shouldn't count on auto-configuration, but I'm wondering why it didn't work this time). In fact this same server would auto-config a 6 disk fibre channel array on booting every time.

Thanks for the help.

Jason M.

---

