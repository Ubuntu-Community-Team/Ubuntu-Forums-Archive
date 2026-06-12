---
title: "Speed issue with RAID-5"
date: 2011-10-24
forum: Server Platforms
---

### Post by Arrouan on 2011-10-24
Hello,

I have a RAID-5 with 3x1.5To HDD (7200Tr 4K Sector). I have speed issue on it. At top speed, I have (at best) 60Mb/s write (20Mo per disk with iostat). Reading speed is ok almost 230Mb/s. But most of the times, the speed is 0Mb/s and the system froze. I upgrade to the last Ubuntu (11.10) but I have the issue since I build the system. I try with and without GUI. I also try the performance script for RAID-5/6 that I found on this forum.

I have an Atom 330 with NVidia ION and 2Gb of RAM (swap is there but not used i.e. 100% Free).

If you have any idea how to fix it.

Thanks in advance

----------------------------

fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
224 heads, 56 sectors/track, 233599 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dd881

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          56      426495      213220   83  Linux
/dev/sda2          426496    42386175    20979840   fd  Linux raid autodetect
/dev/sda3        42386176    46500607     2057216   82  Linux swap / Solaris
/dev/sda4        46500608  2930265855  1441882624   fd  Linux raid autodetect

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
224 heads, 56 sectors/track, 233599 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e0d51

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              56      426495      213220   83  Linux
/dev/sdb2          426496    42386175    20979840   fd  Linux raid autodetect
/dev/sdb3        42386176    46500607     2057216   82  Linux swap / Solaris
/dev/sdb4        46500608  2930265855  1441882624   fd  Linux raid autodetect

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
224 heads, 56 sectors/track, 233599 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              56      426495      213220   83  Linux
/dev/sdc2          426496    42386175    20979840   fd  Linux raid autodetect
/dev/sdc3        42386176    46500607     2057216   82  Linux swap / Solaris
/dev/sdc4        46500608  2930265855  1441882624   fd  Linux raid autodetect

----------------------------

Here is mdadm --detail /dev/md1:
/dev/md1:
        Version : 0.90
  Creation Time : Tue Mar  2 19:06:36 2010
     Raid Level : raid5
     Array Size : 2883765120 (2750.17 GiB 2952.98 GB)
  Used Dev Size : 1441882560 (1375.09 GiB 1476.49 GB)
   Raid Devices : 3                                                          
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon Oct 24 20:04:36 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 5d5ab3f8:4d74a9b0:3d186b3c:53958f34
         Events : 0.1395726

    Number   Major   Minor   RaidDevice State
       0       8       20        0      active sync   /dev/sdb4
       1       8       36        1      active sync   /dev/sdc4
       2       8        4        2      active sync   /dev/sda4

----------------------------

Performance test:
dd if=/dev/zero bs=1024 count=1000000 of=/home/arrouan/test
1000000+0 records in
1000000+0 records out
1024000000 bytes (1.0 GB) copied, 18.2925 s, 56.0 MB/s

dd if=/home/arrouan/test of=/dev/null
2000000+0 records in
2000000+0 records out
1024000000 bytes (1.0 GB) copied, 4.48074 s, 229 MB/s

---

