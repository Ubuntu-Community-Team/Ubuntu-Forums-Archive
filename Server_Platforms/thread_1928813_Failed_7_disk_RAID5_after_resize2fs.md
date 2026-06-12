---
title: "Failed 7 disk RAID5 after resize2fs"
date: 2012-02-20
forum: Server Platforms
---

### Post by wargus on 2012-02-20
Hi All,

I've recently been creating/expanding a 7 disk RAID5 system using these instructions: [http://ubuntuforums.org/showthread.php?t=517282](http://ubuntuforums.org/showthread.php?t=517282) The only difference is that I've been using **EXT4 rather than EXT2** as per the instructions, this is true for both the initial formating and the final file system on the raid device. The array grew successfully from 3 to 5 disks (after which point I added data to the array) and from 5 to 7.

All was going well until the final **sudo resize2fs /dev/md0** command  which has ended up borking the array. Initially mdadm reported that two disks had failed. In a mad panic I also removed from the array another disk (sdf1) using mdadm.

The disk manager reports that all the disks are fine. I assume that my problem is file-system related, but I don't know how to assemble the array to check.
[SIZE=2]
I really need help to:[/SIZE]
[LIST=1]
[*][SIZE=2] Set /dev/sdf1 as an active member of the array instead of a spare,[/SIZE]
[*][SIZE=2] Assemble the array (there appears to be two),[/SIZE]
[*][SIZE=2] Check/rebuild the file system,[/SIZE]
[*][SIZE=2] Set up the array to assemble and mount at boot.[/SIZE]
[/LIST]
 
Here is the output of **sudo mdadm --detail /dev/md0**
```

/dev/md0:
        Version : 1.2
  Creation Time : Tue Feb 14 19:30:43 2012
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 7
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Mon Feb 20 21:20:40 2012
          State : active, FAILED, Not Started
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : files:0  (local to host files)
           UUID : 9ebb9784:e05ed50f:8c657574:132faca8
         Events : 22030

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       65        1      active sync   /dev/sde1
       [B]2       0        0        2      removed
       3       0        0        3      removed
       4       0        0        4      removed[/B]
       7       8       97        5      active sync   /dev/sdg1
       6       8      113        6      active sync   /dev/sdh1

```This is the output of **mdadm --examine /dev/sd[bcdefgh]1**
```

/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9ebb9784:e05ed50f:8c657574:132faca8
           Name : files:0  (local to host files)
  Creation Time : Tue Feb 14 19:30:43 2012
     Raid Level : raid5
   Raid Devices : 7

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 23442143232 (11178.09 GiB 12002.38 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : ac2fd6d2:7debe9e4:fedbebf9:220df2f6

    Update Time : Mon Feb 20 08:37:59 2012
       **Checksum : 4da734fc - correct**
         Events : 22009

         Layout : left-symmetric
     Chunk Size : 512K

   **Device Role : Active device 4**
   **Array State : AAAAAAA ('A' == active, '.' == missing)**

/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9ebb9784:e05ed50f:8c657574:132faca8
           Name : files:0  (local to host files)
  Creation Time : Tue Feb 14 19:30:43 2012
     Raid Level : raid5
   Raid Devices : 7

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 23442143232 (11178.09 GiB 12002.38 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 7d554a16:02b3a8e3:4d2b836d:7b76880c

    Update Time : Mon Feb 20 08:37:59 2012
       **Checksum : 1907daf9 - correct**
         Events : 22009

         Layout : left-symmetric
     Chunk Size : 512K

   [B]Device Role : Active device 3
   Array State : AAAAAAA ('A' == active, '.' == missing)[/B]

/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9ebb9784:e05ed50f:8c657574:132faca8
           Name : files:0  (local to host files)
  Creation Time : Tue Feb 14 19:30:43 2012
     Raid Level : raid5
   Raid Devices : 7

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 23442143232 (11178.09 GiB 12002.38 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 9c2a89bb:cec78348:703f1c69:a32163aa

    Update Time : Mon Feb 20 21:20:40 2012
       **Checksum : bc8e36fc - correct**
         Events : 22030

         Layout : left-symmetric
     Chunk Size : 512K

   [B]Device Role : Active device 0
   Array State : AA...AA ('A' == active, '.' == missing)[/B]

/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9ebb9784:e05ed50f:8c657574:132faca8
           Name : files:0  (local to host files)
  Creation Time : Tue Feb 14 19:30:43 2012
     Raid Level : raid5
   Raid Devices : 7

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 23442143232 (11178.09 GiB 12002.38 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 0c367cb4:2e898415:950c902b:710e8794

    Update Time : Mon Feb 20 21:20:40 2012
      ** Checksum : 2f19bdc0 - correct**
         Events : 22030

         Layout : left-symmetric
     Chunk Size : 512K

   [B]Device Role : Active device 1
   Array State : AA...AA ('A' == active, '.' == missing)[/B]

/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9ebb9784:e05ed50f:8c657574:132faca8
           Name : files:0  (local to host files)
  Creation Time : Tue Feb 14 19:30:43 2012
     Raid Level : raid5
   Raid Devices : 7

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 23442143232 (11178.09 GiB 12002.38 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1be3d8d7:01c0b4ea:53eb468d:73bbb5dd

    Update Time : Mon Feb 20 16:58:31 2012
       **Checksum : d28ceff3 - correct**
         Events : 22029

         Layout : left-symmetric
     Chunk Size : 512K

   [B]Device Role : spare
   Array State : AA...AA ('A' == active, '.' == missing)[/B]

/dev/sdg1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9ebb9784:e05ed50f:8c657574:132faca8
           Name : files:0  (local to host files)
  Creation Time : Tue Feb 14 19:30:43 2012
     Raid Level : raid5
   Raid Devices : 7

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 23442143232 (11178.09 GiB 12002.38 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : b94d8abb:84f3b9a9:1d6d3a70:f912f08f

    Update Time : Mon Feb 20 21:20:40 2012
       **Checksum : a70a4da - correct**
         Events : 22030

         Layout : left-symmetric
     Chunk Size : 512K

  [B] Device Role : Active device 5
   Array State : AA...AA ('A' == active, '.' == missing)[/B]

/dev/sdh1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9ebb9784:e05ed50f:8c657574:132faca8
           Name : files:0  (local to host files)
  Creation Time : Tue Feb 14 19:30:43 2012
     Raid Level : raid5
   Raid Devices : 7

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 23442143232 (11178.09 GiB 12002.38 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 9e8b6884:cc4ab2c8:5ea96ba9:3b3de001

    Update Time : Mon Feb 20 21:20:40 2012
      ** Checksum : 9d68a088 - correct**
         Events : 22030

         Layout : left-symmetric
     Chunk Size : 512K

   [B]Device Role : Active device 6
   Array State : AA...AA ('A' == active, '.' == missing)[/B]

```Any assistance would be greatly appreciated,

-Warren

---

### Post by rubylaser on 2012-02-21
This thread is marked solved. Has this actually been fixed?

---

