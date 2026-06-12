---
title: "Major Raid Problems"
date: 2011-04-16
forum: Server Platforms
---

### Post by samurailink3 on 2011-04-16
Looks like a bad e-sata card borked my array. Here is the last examine output from mdadm. I've been trying to put these drives back into the correct order for some time now with 'mdadm --create --assume-clean' then seeing if it was a mountable crypt filesystem (Raid device was encrypted).

```
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d2d81657:b473c537:89702771:449649de
  Creation Time : Sat Nov  6 00:14:29 2010
     Raid Level : raid1
  Used Dev Size : 976760768 (931.51 GiB 1000.20 GB)
     Array Size : 976760768 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sat Apr 16 21:00:36 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d334dffc - correct
         Events : 242


      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d2d81657:b473c537:89702771:449649de
  Creation Time : Sat Nov  6 00:14:29 2010
     Raid Level : raid1
  Used Dev Size : 976760768 (931.51 GiB 1000.20 GB)
     Array Size : 976760768 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sat Apr 16 21:00:36 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d334e00e - correct
         Events : 242


      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : dd4f7de1:a4c3bf73:89a35d79:15aad3d5
           Name : :TARDIS
  Creation Time : Fri Oct 22 23:26:28 2010
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 1953519730 (931.51 GiB 1000.20 GB)
     Array Size : 13674637312 (6520.58 GiB 7001.41 GB)
  Used Dev Size : 1953519616 (931.51 GiB 1000.20 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 9c202983:4475f095:e15b5d71:c0a94593

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 16 15:31:51 2011
       Checksum : 41427ec6 - correct
         Events : 236902

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 10 (0, 1, 2, 3, failed, failed, failed, failed, 7, 5)
   Array State : uuuu_u_u 4 failed
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0b878609:91044297:fd11a037:1a4a15db
           Name : :ExtraLife
  Creation Time : Fri Nov 26 23:46:36 2010
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 1953519730 (931.51 GiB 1000.20 GB)
     Array Size : 1953519730 (931.51 GiB 1000.20 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 2bf1edd3:e21c3a6d:a086e681:aaf7dafc

    Update Time : Sat Apr 16 16:24:42 2011
       Checksum : 7dd40b62 - correct
         Events : 140


    Array Slot : 1 (0, 1)
   Array State : uU
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0b878609:91044297:fd11a037:1a4a15db
           Name : :ExtraLife
  Creation Time : Fri Nov 26 23:46:36 2010
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 1953519730 (931.51 GiB 1000.20 GB)
     Array Size : 1953519730 (931.51 GiB 1000.20 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 7b46a8ab:b6b08bb2:f7a28fa6:2afb547b

    Update Time : Sat Apr 16 16:24:42 2011
       Checksum : 3e03145c - correct
         Events : 140


    Array Slot : 0 (0, 1)
   Array State : Uu
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : dd4f7de1:a4c3bf73:89a35d79:15aad3d5
           Name : :TARDIS
  Creation Time : Fri Oct 22 23:26:28 2010
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 1953519730 (931.51 GiB 1000.20 GB)
     Array Size : 13674637312 (6520.58 GiB 7001.41 GB)
  Used Dev Size : 1953519616 (931.51 GiB 1000.20 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ca9fcab5:8d4d3edf:758bb57e:bd1416dc

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 16 15:31:51 2011
       Checksum : 135a70d6 - correct
         Events : 236920

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 0 (0, 1, 2, 3, failed, failed, failed, failed, 7, 5, failed)
   Array State : Uuuu_u_u 5 failed
/dev/sdg1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : dd4f7de1:a4c3bf73:89a35d79:15aad3d5
           Name : :TARDIS
  Creation Time : Fri Oct 22 23:26:28 2010
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 1953519730 (931.51 GiB 1000.20 GB)
     Array Size : 13674637312 (6520.58 GiB 7001.41 GB)
  Used Dev Size : 1953519616 (931.51 GiB 1000.20 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : d1e493f5:cf70724b:d07099c0:0d30084f

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 16 15:31:51 2011
       Checksum : 7429d9c3 - correct
         Events : 236920

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 2 (0, 1, 2, failed, failed, failed, failed, failed, failed, 5, failed)
   Array State : uuU__u__ 7 failed
/dev/sdh1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : dd4f7de1:a4c3bf73:89a35d79:15aad3d5
           Name : :TARDIS
  Creation Time : Fri Oct 22 23:26:28 2010
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 1953519730 (931.51 GiB 1000.20 GB)
     Array Size : 13674637312 (6520.58 GiB 7001.41 GB)
  Used Dev Size : 1953519616 (931.51 GiB 1000.20 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 229a3027:712eaa0c:bac7d25f:282a5ef1

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 16 15:31:51 2011
       Checksum : a88d9db9 - correct
         Events : 236920

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 1 (0, 1, 2, failed, failed, failed, failed, failed, failed, 5, failed)
   Array State : uUu__u__ 7 failed
/dev/sdi1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : dd4f7de1:a4c3bf73:89a35d79:15aad3d5
           Name : :TARDIS
  Creation Time : Fri Oct 22 23:26:28 2010
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 1953519730 (931.51 GiB 1000.20 GB)
     Array Size : 13674637312 (6520.58 GiB 7001.41 GB)
  Used Dev Size : 1953519616 (931.51 GiB 1000.20 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 71d51db6:40ba08d8:704a2bec:b9a0a430

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 16 15:31:51 2011
       Checksum : ce785e27 - correct
         Events : 236920

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 9 (0, 1, 2, failed, failed, failed, failed, failed, failed, 5, failed)
   Array State : uuu__U__ 7 failed
/dev/sdj1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : dd4f7de1:a4c3bf73:89a35d79:15aad3d5
           Name : :TARDIS
  Creation Time : Fri Oct 22 23:26:28 2010
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 1953519730 (931.51 GiB 1000.20 GB)
     Array Size : 13674637312 (6520.58 GiB 7001.41 GB)
  Used Dev Size : 1953519616 (931.51 GiB 1000.20 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : f20e3125:6b891240:1676df1b:1393d8aa

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 16 15:31:51 2011
       Checksum : 4f8184cd - correct
         Events : 236910

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 5 (0, 1, 2, 3, failed, failed, failed, failed, 7, 5)
   Array State : uuuu_u_u 4 failed
/dev/sdk1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : dd4f7de1:a4c3bf73:89a35d79:15aad3d5
           Name : :TARDIS
  Creation Time : Fri Oct 22 23:26:28 2010
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 1953519730 (931.51 GiB 1000.20 GB)
     Array Size : 13674637312 (6520.58 GiB 7001.41 GB)
  Used Dev Size : 1953519616 (931.51 GiB 1000.20 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 96fb1f69:dc19343b:cf44e95e:00bb12fb

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 16 12:54:18 2011
       Checksum : 21dad3b0 - correct
         Events : 236920

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 8 (0, 1, 2, 3, failed, 4, 6, failed, 7, 5)
   Array State : uuuuuuuU 2 failed
/dev/sdl1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : dd4f7de1:a4c3bf73:89a35d79:15aad3d5
           Name : :TARDIS
  Creation Time : Fri Oct 22 23:26:28 2010
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 1953519730 (931.51 GiB 1000.20 GB)
     Array Size : 13674637312 (6520.58 GiB 7001.41 GB)
  Used Dev Size : 1953519616 (931.51 GiB 1000.20 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : e7115f35:ee08b97a:6ec0f7e6:47442d84

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 16 15:31:51 2011
       Checksum : 3ec302d3 - correct
         Events : 236910

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 6 (0, 1, 2, 3, failed, failed, failed, failed, 7, 5)
   Array State : uuuu_u_u 4 failed
/dev/sdm1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : dd4f7de1:a4c3bf73:89a35d79:15aad3d5
           Name : :TARDIS
  Creation Time : Fri Oct 22 23:26:28 2010
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 1953519730 (931.51 GiB 1000.20 GB)
     Array Size : 13674637312 (6520.58 GiB 7001.41 GB)
  Used Dev Size : 1953519616 (931.51 GiB 1000.20 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 7f326855:fff44128:6430fd17:940956e1

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 16 12:54:18 2011
       Checksum : 9a881fdf - correct
         Events : 236920

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 3 (0, 1, 2, 3, failed, 4, 6, failed, 7, 5)
   Array State : uuuUuuuu 2 failed

```

I'm trying to recreate the TARDIS array. Any suggestions, or have I lost 7TB of data? :(

Thanks for any suggestions or ideas!
(Oh, and I'm running the latest updates on 10.04LTS Server)

---

### Post by MakOwner on 2011-04-16
I had this happen to me once.

There is a "force" parameter to the assemble command.

```

Options that are valid with --assemble (-A) are:
  --bitmap=          : bitmap file to use wit the array
  --uuid=       -u   : uuid of array to assemble. Devices which don't
                       have this uuid are excluded
  --super-minor= -m  : minor number to look for in super-block when
                       choosing devices to use.
  --name=       -N   : Array name to look for in super-block.
  --config=     -c   : config file
  --scan        -s   : scan config file for missing information
  --run         -R   : Try to start the array even if not enough devices
                       for a full array are present
  --force       -f   : Assemble the array even if some superblocks appear
                     : out-of-date.  This involves modifying the superblocks.
  --update=     -U   : Update superblock: try '-A --update=?' for option list.
  --no-degraded      : Assemble but do not start degraded arrays.

```

---

### Post by samurailink3 on 2011-04-16
I was using the --force command, but it complained that some devices were out of date. I have since tried with the --create command, but it (obviously) overwrote the old raid settings. I now have to create the raid by hand using this old examine data, but I'm confused because disk 4 and 7 are missing in the position lists and disks 8 and 9 showed up, but clearly shouldn't be part of an array with only 8 disks (device positions should be 0-7).

---

