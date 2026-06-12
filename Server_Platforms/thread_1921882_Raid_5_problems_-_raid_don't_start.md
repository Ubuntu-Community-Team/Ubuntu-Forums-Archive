---
title: "Raid 5 problems - raid don't start"
date: 2012-02-07
forum: Server Platforms
---

### Post by pedromiguelpg on 2012-02-07
Change one disk /dev/sdf to /dev/sdf1 and resync, process 100% ok
when remove the disk /dev/sdc,  the disk /dev/sdf1 made to not appear
 
information of the md0:

mdadm: looking for devices for /dev/md0
mdadm: /dev/sda1 is identified as a member of /dev/md0, slot 5.
mdadm: /dev/sdg1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdh1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdi1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdj1 is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 7.
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 8.
mdadm: added /dev/sdg1 to /dev/md0 as 1
mdadm: added /dev/sdi1 to /dev/md0 as 2
mdadm: no uptodate device for slot 3 of /dev/md0
mdadm: added /dev/sdj1 to /dev/md0 as 4
mdadm: added /dev/sda1 to /dev/md0 as 5
mdadm: no uptodate device for slot 6 of /dev/md0
mdadm: added /dev/sdd to /dev/md0 as 7
mdadm: added /dev/sdb to /dev/md0 as 8
mdadm: added /dev/sdh1 to /dev/md0 as 0
mdadm: /dev/md0 assembled from 7 drives - not enough to start the array.

[root@storage ~]# mdadm --examine /dev/sdf
/dev/sdf:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 0976ae8c:7ae1bfa6:43d8af5f:dfa816ff
  Creation Time : Sun Dec 14 15:33:28 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 7814079488 (7452.09 GiB 8001.62 GB)
   Raid Devices : 9
  Total Devices : 9
Preferred Minor : 0
    Update Time : Sat Feb  4 16:27:49 2012
          State : active
 Active Devices : 9
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 240c0018 - correct
         Events : 3007481
         Layout : left-symmetric
     Chunk Size : 64K
      Number   Major   Minor   RaidDevice State
this     6       8       80        6      active sync   /dev/sdf
   0     0       8      113        0      active sync   /dev/sdh1
   1     1       8       97        1      active sync   /dev/sdg1
   2     2       8      129        2      active sync   /dev/sdi1
   3     3       8       32        3      active sync   /dev/sdc
   4     4       8      145        4      active sync   /dev/sdj1
   5     5       8        1        5      active sync   /dev/sda1
   6     6       8       80        6      active sync   /dev/sdf
   7     7       8       48        7      active sync   /dev/sdd
   8     8       8       16        8      active sync   /dev/sdb
 
 
[root@storage ~]# fdisk -l /dev/sdf
Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121601   976760001   fd  Linux raid autodetect
 
Thanks

---

### Post by rubylaser on 2012-02-07
Did you zero the superblock on /dev/sdf before you added /dev/sdf1 to the array? If not, I'd remove that disk from the system, reboot, and reassemble the array degraded.  Zero the superblock on the /dev/sdf and /dev/sdf1, and then add /dev/sdf1 back to the array.

---

### Post by pedromiguelpg on 2012-02-08
i have another disk remove from the raid disk number 3, and if remove the sdf i will have 2 fails disk, and the raid will work end i re-add the disk?

---

### Post by rubylaser on 2012-02-08
I need more info, can you give me the output of these commands?

```
cat /proc/mdstat
cat /etc/mdadm/mdadm.conf
mdadm --detail /dev/md0
mdadm -E /dev/sd[aghij]1 /dev/sd[bd]
```

As a sidebar, a 9 disk RAID5 is just asking for trouble in the long run.  Resyncs take a long time, and it's a real possibility that you'll lose another disk during a resync.  I'd consider adding another disk and turning this into a RAID6.

---

### Post by pedromiguelpg on 2012-02-08
The results of the output commands:

[root@storage ~]# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md0 : inactive sdj1[4] sdi1[2] sdh1[0] sdg1[1] sdf1[6] sda1[5]
      5860559616 blocks
unused devices: <none>
[root@storage ~]# cat /etc/mdadm/mdadm.conf
ARRAY /dev/md0 level=raid5 num-devices=9 UUID=0976ae8c:7ae1bfa6:43d8af5f:dfa816ff
[root@storage ~]# mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Sun Dec 14 15:33:28 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 9
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent
    Update Time : Mon Feb  6 16:46:57 2012
          State : active, degraded, Not Started
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
         Layout : left-symmetric
     Chunk Size : 64K
           UUID : 0976ae8c:7ae1bfa6:43d8af5f:dfa816ff
         Events : 0.3011492
    Number   Major   Minor   RaidDevice State
       0       8      113        0      active sync   /dev/sdh1
       1       8       97        1      active sync   /dev/sdg1
       2       8      129        2      active sync   /dev/sdi1
       3       0        0        3      removed
       4       8      145        4      active sync   /dev/sdj1
       5       8        1        5      active sync   /dev/sda1
       6       8       81        6      active sync   /dev/sdf1
       7       0        0        7      removed
       8       0        0        8      removed
[root@storage ~]#
[root@storage ~]# mdadm -E  /dev/sd[bd]
/dev/sdb:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 0976ae8c:7ae1bfa6:43d8af5f:dfa816ff
  Creation Time : Sun Dec 14 15:33:28 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 7814079488 (7452.09 GiB 8001.62 GB)
   Raid Devices : 9
  Total Devices : 9
Preferred Minor : 0
    Update Time : Mon Feb  6 16:46:57 2012
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 240ec6c5 - correct
         Events : 3011492
         Layout : left-symmetric
     Chunk Size : 64K
      Number   Major   Minor   RaidDevice State
this     8       8       16        8      active sync   /dev/sdb
   0     0       8      113        0      active sync   /dev/sdh1
   1     1       8       97        1      active sync   /dev/sdg1
   2     2       8      129        2      active sync   /dev/sdi1
   3     3       0        0        3      faulty removed
   4     4       8      145        4      active sync   /dev/sdj1
   5     5       8        1        5      active sync   /dev/sda1
   6     6       8       81        6      active sync   /dev/sdf1
   7     7       8       48        7      active sync   /dev/sdd
   8     8       8       16        8      active sync   /dev/sdb
/dev/sdd:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 0976ae8c:7ae1bfa6:43d8af5f:dfa816ff
  Creation Time : Sun Dec 14 15:33:28 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 7814079488 (7452.09 GiB 8001.62 GB)
   Raid Devices : 9
  Total Devices : 9
Preferred Minor : 0
    Update Time : Mon Feb  6 16:46:57 2012
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 240ec6e3 - correct
         Events : 3011492
         Layout : left-symmetric
     Chunk Size : 64K
      Number   Major   Minor   RaidDevice State
this     7       8       48        7      active sync   /dev/sdd
   0     0       8      113        0      active sync   /dev/sdh1
   1     1       8       97        1      active sync   /dev/sdg1
   2     2       8      129        2      active sync   /dev/sdi1
   3     3       0        0        3      faulty removed
   4     4       8      145        4      active sync   /dev/sdj1
   5     5       8        1        5      active sync   /dev/sda1
   6     6       8       81        6      active sync   /dev/sdf1
   7     7       8       48        7      active sync   /dev/sdd
   8     8       8       16        8      active sync   /dev/sdb

[root@storage ~]# mdadm -E /dev/sd[aghij]1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 0976ae8c:7ae1bfa6:43d8af5f:dfa816ff
  Creation Time : Sun Dec 14 15:33:28 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 7814079488 (7452.09 GiB 8001.62 GB)
   Raid Devices : 9
  Total Devices : 9
Preferred Minor : 0
    Update Time : Mon Feb  6 16:46:57 2012
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 240ec6b0 - correct
         Events : 3011492
         Layout : left-symmetric
     Chunk Size : 64K
      Number   Major   Minor   RaidDevice State
this     5       8        1        5      active sync   /dev/sda1
   0     0       8      113        0      active sync   /dev/sdh1
   1     1       8       97        1      active sync   /dev/sdg1
   2     2       8      129        2      active sync   /dev/sdi1
   3     3       0        0        3      faulty removed
   4     4       8      145        4      active sync   /dev/sdj1
   5     5       8        1        5      active sync   /dev/sda1
   6     6       8       81        6      active sync   /dev/sdf1
   7     7       8       48        7      active sync   /dev/sdd
   8     8       8       16        8      active sync   /dev/sdb
/dev/sdg1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 0976ae8c:7ae1bfa6:43d8af5f:dfa816ff
  Creation Time : Sun Dec 14 15:33:28 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 7814079488 (7452.09 GiB 8001.62 GB)
   Raid Devices : 9
  Total Devices : 9
Preferred Minor : 0
    Update Time : Mon Feb  6 16:46:57 2012
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 240ec708 - correct
         Events : 3011492
         Layout : left-symmetric
     Chunk Size : 64K
      Number   Major   Minor   RaidDevice State
this     1       8       97        1      active sync   /dev/sdg1
   0     0       8      113        0      active sync   /dev/sdh1
   1     1       8       97        1      active sync   /dev/sdg1
   2     2       8      129        2      active sync   /dev/sdi1
   3     3       0        0        3      faulty removed
   4     4       8      145        4      active sync   /dev/sdj1
   5     5       8        1        5      active sync   /dev/sda1
   6     6       8       81        6      active sync   /dev/sdf1
   7     7       8       48        7      active sync   /dev/sdd
   8     8       8       16        8      active sync   /dev/sdb
/dev/sdh1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 0976ae8c:7ae1bfa6:43d8af5f:dfa816ff
  Creation Time : Sun Dec 14 15:33:28 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 7814079488 (7452.09 GiB 8001.62 GB)
   Raid Devices : 9
  Total Devices : 9
Preferred Minor : 0
    Update Time : Mon Feb  6 16:46:57 2012
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 240ec716 - correct
         Events : 3011492
         Layout : left-symmetric
     Chunk Size : 64K
      Number   Major   Minor   RaidDevice State
this     0       8      113        0      active sync   /dev/sdh1
   0     0       8      113        0      active sync   /dev/sdh1
   1     1       8       97        1      active sync   /dev/sdg1
   2     2       8      129        2      active sync   /dev/sdi1
   3     3       0        0        3      faulty removed
   4     4       8      145        4      active sync   /dev/sdj1
   5     5       8        1        5      active sync   /dev/sda1
   6     6       8       81        6      active sync   /dev/sdf1
   7     7       8       48        7      active sync   /dev/sdd
   8     8       8       16        8      active sync   /dev/sdb
/dev/sdi1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 0976ae8c:7ae1bfa6:43d8af5f:dfa816ff
  Creation Time : Sun Dec 14 15:33:28 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 7814079488 (7452.09 GiB 8001.62 GB)
   Raid Devices : 9
  Total Devices : 9
Preferred Minor : 0
    Update Time : Mon Feb  6 16:46:57 2012
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 240ec72a - correct
         Events : 3011492
         Layout : left-symmetric
     Chunk Size : 64K
      Number   Major   Minor   RaidDevice State
this     2       8      129        2      active sync   /dev/sdi1
   0     0       8      113        0      active sync   /dev/sdh1
   1     1       8       97        1      active sync   /dev/sdg1
   2     2       8      129        2      active sync   /dev/sdi1
   3     3       0        0        3      faulty removed
   4     4       8      145        4      active sync   /dev/sdj1
   5     5       8        1        5      active sync   /dev/sda1
   6     6       8       81        6      active sync   /dev/sdf1
   7     7       8       48        7      active sync   /dev/sdd
   8     8       8       16        8      active sync   /dev/sdb
/dev/sdj1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 0976ae8c:7ae1bfa6:43d8af5f:dfa816ff
  Creation Time : Sun Dec 14 15:33:28 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 7814079488 (7452.09 GiB 8001.62 GB)
   Raid Devices : 9
  Total Devices : 9
Preferred Minor : 0
    Update Time : Mon Feb  6 16:46:57 2012
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 240ec73e - correct
         Events : 3011492
         Layout : left-symmetric
     Chunk Size : 64K
      Number   Major   Minor   RaidDevice State
this     4       8      145        4      active sync   /dev/sdj1
   0     0       8      113        0      active sync   /dev/sdh1
   1     1       8       97        1      active sync   /dev/sdg1
   2     2       8      129        2      active sync   /dev/sdi1
   3     3       0        0        3      faulty removed
   4     4       8      145        4      active sync   /dev/sdj1
   5     5       8        1        5      active sync   /dev/sda1
   6     6       8       81        6      active sync   /dev/sdf1
   7     7       8       48        7      active sync   /dev/sdd
   8     8       8       16        8      active sync   /dev/sdb

---

### Post by pedromiguelpg on 2012-02-09
SOLVED
 
mdadm --assemble --scan -fv
 
and find the disk sdf have 2 superblock 
 

mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 6.
mdadm: /dev/sdf is identified as a member of /dev/md0, slot 6.
 
and need to remove one: 
 
mdadm --zero-superblock /dev/sdf
 
Assemble raid:
 
mdadm --assemble --scan -fv
cat /proc/mdstat 
 

Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 sdh1[0] sdb[8] sdd[7] sda1[5] sdj1[4] sdc[3] sdi1[2] sdg1[1]
      7814079488 blocks level 5, 64k chunk, algorithm 2 [9/8] [UUUUUU_UU]
      
problem resolved, thanks for all.

---

### Post by rubylaser on 2012-02-10
No problem, that's what I was trying to tell you the problem was earlier when I asked if you zeroed the superblock on /dev/sdf.  I'm glad you got it solved.

---

