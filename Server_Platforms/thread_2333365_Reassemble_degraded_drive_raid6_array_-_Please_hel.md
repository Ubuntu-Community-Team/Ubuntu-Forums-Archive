---
title: "Reassemble degraded drive raid6 array - Please help"
date: 2016-08-09
forum: Server Platforms
---

### Post by kmcclure on 2016-08-09
Please help!

I have a raid6 array with 24 drives that was rebuilding on /dev/sdq2 and /dev/sdK2  simultaneously, when the third drive /dev/sdo2 dropped out.  There are no bad blocks or errors on the /dev/sdo2.  How do I re-assemble the array using the good drives plus /dev/sdo2 to allow the rebuild to continue?

```
XXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXX

cat /proc/mdstat
md3 : active raid6 sda2[30] sdq2[29] sdu2[28] sdg2[24] sdb2[27] sdd2[26] sdn2[25] sdo2[14](F) sdt2[19] sdm2[12] sdw2[22] sdi2[8] sdf2[5] sds2[18] sdv2[21] sdr2[17] sdp2[15] sdx2[23] sdl2[11] sdk2[10](F) sdh2[7] sdj2[9] sdc2[2] sde2[4]
      61411924224 blocks super 1.2 level 6, 256k chunk, algorithm 2 [23/20] [UUUUUUUUUU_UUU_U_UUUUUU]
        resync=DELAYED



XXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXX


 mdadm -D /dev/md3
/dev/md3:
        Version : 1.2
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 2924377344 (2788.90 GiB 2994.56 GB)
   Raid Devices : 23
  Total Devices : 24
    Persistence : Superblock is persistent

    Update Time : Tue Aug  9 13:37:12 2016
          State : clean, FAILED, resyncing (DELAYED)
 Active Devices : 20
Working Devices : 22
 Failed Devices : 2
  Spare Devices : 2

         Layout : left-symmetric
     Chunk Size : 256K

           Name : storage28:3  (local to host storage28)
           UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
         Events : 1548933

    Number   Major   Minor   RaidDevice State
      28      65       66        0      active sync   /dev/sdu2
      25       8      210        1      active sync   /dev/sdn2
       2       8       34        2      active sync   /dev/sdc2
      26       8       50        3      active sync   /dev/sdd2
       4       8       66        4      active sync   /dev/sde2
       5       8       82        5      active sync   /dev/sdf2
      23      65      114        6      active sync   /dev/sdx2
       7       8      114        7      active sync   /dev/sdh2
       8       8      130        8      active sync   /dev/sdi2
       9       8      146        9      active sync   /dev/sdj2
      30       8        2       10      spare rebuilding   /dev/sda2
      11       8      178       11      active sync   /dev/sdl2
      12       8      194       12      active sync   /dev/sdm2
      24       8       98       13      active sync   /dev/sdg2
      14       0        0       14      removed
      15       8      242       15      active sync   /dev/sdp2
      29      65        2       16      spare rebuilding   /dev/sdq2
      17      65       18       17      active sync   /dev/sdr2
      18      65       34       18      active sync   /dev/sds2
      19      65       50       19      active sync   /dev/sdt2
      27       8       18       20      active sync   /dev/sdb2
      21      65       82       21      active sync   /dev/sdv2
      22      65       98       22      active sync   /dev/sdw2

      10       8      162        -      faulty spare   /dev/sdk2
      14       8      226        -      faulty spare   /dev/sdo2




XXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXX


mdadm --examine /dev/sd[abcdefghijklmnopqrstuvwx]2
/dev/sda2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x2
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
Recovery Offset : 397114624 sectors
          State : clean
    Device UUID : 9bf8f954:16931323:2006beeb:70ecc504

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 292543bd - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 10
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdb2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 7f939e83:71c5f3fb:6a152417:2b021f42

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 81bdb8fc - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 20
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdc2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f1570d33:b7c259a8:b760a79a:02241c26

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 4512e7bf - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 2
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdd2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 29a54db6:6c918097:189aa7aa:e0db1b4a

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : eb79f503 - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 3
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sde2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 20fe04ab:bf6ce374:ee01083f:4a955bfd

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 5344a78 - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 4
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdf2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 4fbd5f25:9908bbb4:3bece7bb:9f8a73ab

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : ea5e8523 - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 5
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdg2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 7781f768:21f0c149:732e4ba1:1e61697c

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 7956499d - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 13
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdh2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 02e8b57f:6664d608:a143b0c4:b02b3060

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 5655041c - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 7
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdi2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a2f3c993:9defdda8:8c5b721e:6b175530

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 34579e9a - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 8
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdj2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 167a7b65:de35a4ad:a97db876:aed1a4ad

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : e06547b0 - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 9
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdk2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 629874de:7a047deb:a6d27c7d:3d7eadd7

    Update Time : Tue Aug  9 03:54:51 2016
       Checksum : c8027647 - correct
         Events : 1528533

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 10
   Array State : AAAAAAAAAAAAAAAAAAAAAAA ('A' == active, '.' == missing)
/dev/sdl2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 5e97798b:3facc192:bd7e5cf1:27ed5749

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 1d7f7e9 - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 11
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdm2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 2588101e:c59272ec:16a2fc9a:2ba8ffce

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 1d67ad94 - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 12
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdn2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e0b792e1:8b44b860:450ee28a:458b9c8e

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 4b1de6b - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 1
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdo2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : f5ab1cd9:fbeed708:139e7b8e:b3bf3e10

    Update Time : Tue Aug  9 10:32:39 2016
       Checksum : 29962dfe - correct
         Events : 1548887

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 14
   Array State : AAAAAAAAAAAAAAAAAAAAAAA ('A' == active, '.' == missing)
/dev/sdp2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 10608663:31c7d5b7:4d288fde:b0492458

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : faf7e1a9 - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 15
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdq2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x2
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
Recovery Offset : 397114624 sectors
          State : clean
    Device UUID : 5df3bf29:354bc5db:6e96ea52:c089ca3c

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 55ce243b - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 16
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdr2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : d6e1b3bc:7cf17adb:bbe70560:e8fec46f

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 10e20263 - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 17
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sds2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b5d006fe:e1f5846f:e296b879:a5c947e3

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 73746f8c - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 18
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdt2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 53b27f6b:5a7deb3e:51bfb0ca:71e84eac

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : ca531fde - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 19
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdu2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 377b1346:acf4f1a5:977c6ec6:6ccea9d4

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 3006035f - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 0
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdv2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 373a4b19:d1faea83:e0ab15e5:97bc0175

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : a035e5f0 - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 21
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdw2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a920db20:51df8526:9a61812e:5167b9f0

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : f841157 - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 22
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
/dev/sdx2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 1aa37fda:e98a8b46:4db90d83:64d3b94e
           Name : storage28:3  (local to host storage28)
  Creation Time : Mon Dec 28 16:57:01 2015
     Raid Level : raid6
   Raid Devices : 23

 Avail Dev Size : 5848755343 (2788.90 GiB 2994.56 GB)
     Array Size : 61411924224 (58566.98 GiB 62885.81 GB)
  Used Dev Size : 5848754688 (2788.90 GiB 2994.56 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 8e272fef:062ddc44:709beb16:0ff4598b

    Update Time : Tue Aug  9 11:53:49 2016
       Checksum : 7f392c86 - correct
         Events : 1548931

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 6
   Array State : AAAAAAAAAAAAAA.AAAAAAAA ('A' == active, '.' == missing)
```

---

### Post by darkod on 2016-08-09
You can try something like this: [http://zackreed.me/articles/50-recovery-from-a-multiple-disk-failure-with-mdadm](http://zackreed.me/articles/50-recovery-from-a-multiple-disk-failure-with-mdadm)

24 drives in one array??? Man you are asking for trouble... Plus you allowed two failures before replacing drives?

---

### Post by QIII on 2016-08-09
Please enclose all messages from the terminal in code tags.

1.  Click the # symbol above the text input box and place your cursor in the middle to type or paste your text.

2.  Type or paste your text, then highlight it and click the # symbol.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

---

### Post by kmcclure on 2016-08-09
We actually had three drives drop out within a few hours time.  So even though we have a hot spare, the array couldn't rebuild fast enough between drop outs.

I've tested out the mdadm --assemble --force option on a test box, and it does just what I need.  However, I'm not able to get exclusive access to this array on the server to be able to stop the array.  Is there a way I can restart the server without mdadm automatically re-assembling the array?  Stoping mdadm entirely is not an option since the boot volume is on md0.  Thanks!

---

### Post by darkod on 2016-08-09
I think if you comment out the md3 ARRAY definition in /etc/mdadm/mdadm.conf (put a # in front) it will not try to assemble it on reboot...

Right now it's failed and not rebuilding any more, right? Because if it's still trying to rebuild then it would be a good idea to reboot the server in the middle of it.

Also, I fail to understand why are you not able to stop the array, especially when it's failed??? You have sudo rights, right? Otherwise how do you plan to work on it or reboot the server?

PS- Use the --examine output you posted above and compare the Events counter on each partition. Then I would try to assemble using the minimum number of members, and the ones that have "best" event counters (as close as possible to the "good" members). If it works assembling with minimum members, you can start adding one by one... I'm not sure if the best idea would be to add one member only and wait for rebuild to finish. And only then add the second one that is missing... And then any hot spare(s).

---

### Post by kmcclure on 2016-08-19
Actually, I had root access, but I couldn't get exclusive access to the array to stop it.  All methods of determining what was accessing it were inconclusive.  We had to reboot the server to stop the raid.

_Below is my solution to get the raid volume back up.  I tested this process on a test box before doing it on the real server, which is critical._  This is just to help anyone else who may be in a similar situation.

In my testing, the raid array will assemble with failed drives on reboot, even with enough failed drives to take it the raid off-line.  The only thing that will prevent re-assembly is to actually run the following command on the failed drives so that there are at least three drives in the raid6 that are removed. 
```

mdadm --manage /dev/mdX --remove /dev/sdX 

```

Also, you need to get the array UUID using the following command before stopping the array.
```

mdadm -D /dev/mdX

```

Then after reboot, stop the array.  It will be started even though it isn't assembled.
```

mdadm --stop /dev/mdX

```

I ran the following command to check the drives to make sure they all had the same event count.
```

mdadm -E /dev/sd*2 | grep Events

```

Then I re-assembled the raid using all of the good drives and the last drive (third drive) to drop out of the array.
```

mdadm --assemble --force -u UUID /dev/md3 /dev/sdb2 /dev/sdc2 ......

```

After this, I added the new spares and the array began rebuilding one at a time.  The volume finished rebuilding, and the data is ok.  _Again, it is critical to test this on a test system or VM before trying it on a real server in a recovery situation!_

---

### Post by darkod on 2016-08-19
Great, you did excellent. That was the correct procedure to run...

Please mark the thread as Solved. You can do that in Thread Tools above the first post.

---

