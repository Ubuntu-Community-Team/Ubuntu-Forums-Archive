---
title: "Trying to rescue data from RAID 5"
date: 2014-03-13
forum: Server Platforms
---

### Post by gareth6 on 2014-03-13
Hi,

I am in serious trouble and desperate to savage my data from my RAID server. It was showing degraded at first. But and accidental power cycle now shows NO RAID.
Will any kind soul please help me. I have googled for methods and searched thru the forums. But I not able to find a way out. 

```
root@ubuntu:/home/ubuntu# mdadm --examine --scan -v
ARRAY /dev/md0 level=raid1 num-devices=4 UUID=5a07027a:b965536d:a9e3ebcc:f3ad63a9
   devices=/dev/sdd1,/dev/sdc1,/dev/sdb1,/dev/sda1
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=5b8e231f:cc0a4ab6:aebd925c:1f1edef4
   spares=1   devices=/dev/sdd2,/dev/sdc2,/dev/sdb2,/dev/sda2

```

```
root@ubuntu:/home/ubuntu# mdadm --examine /dev/sd[abcd]1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 5a07027a:b965536d:a9e3ebcc:f3ad63a9
  Creation Time : Wed Mar 12 00:53:37 2014
     Raid Level : raid1
  Used Dev Size : 1959808 (1914.20 MiB 2006.84 MB)
     Array Size : 1959808 (1914.20 MiB 2006.84 MB)
   Raid Devices : 4
  Total Devices : 1
Preferred Minor : 0

    Update Time : Wed Mar 12 03:44:04 2014
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 86653c - correct
         Events : 30


      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8       49        3      active sync   /dev/sdd1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 5a07027a:b965536d:a9e3ebcc:f3ad63a9
  Creation Time : Wed Mar 12 00:53:37 2014
     Raid Level : raid1
  Used Dev Size : 1959808 (1914.20 MiB 2006.84 MB)
     Array Size : 1959808 (1914.20 MiB 2006.84 MB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Mar 12 00:55:59 2014
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 863db3 - correct
         Events : 2


      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 5a07027a:b965536d:a9e3ebcc:f3ad63a9
  Creation Time : Wed Mar 12 00:53:37 2014
     Raid Level : raid1
  Used Dev Size : 1959808 (1914.20 MiB 2006.84 MB)
     Array Size : 1959808 (1914.20 MiB 2006.84 MB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Mar 12 00:55:59 2014
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 863df1 - correct
         Events : 4


      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 5a07027a:b965536d:a9e3ebcc:f3ad63a9
  Creation Time : Wed Mar 12 00:53:37 2014
     Raid Level : raid1
  Used Dev Size : 1959808 (1914.20 MiB 2006.84 MB)
     Array Size : 1959808 (1914.20 MiB 2006.84 MB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Mar 12 00:55:59 2014
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 863dc5 - correct
         Events : 2


      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1


```

```
root@ubuntu:/home/ubuntu# mdadm --assemble --scan -v
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sdf1: Device or resource busy
mdadm: cannot open device /dev/sdf: Device or resource busy
mdadm: cannot open device /dev/sde5: Device or resource busy
mdadm: Cannot assemble mbr metadata on /dev/sde2
mdadm: no recogniseable superblock on /dev/sde1
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sdd2 has wrong uuid.
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: /dev/sdc2 has wrong uuid.
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdb2 has wrong uuid.
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: cannot open device /dev/loop0: Device or resource busy
mdadm: looking for devices for /dev/md1
mdadm: cannot open device /dev/sdf1: Device or resource busy
mdadm: cannot open device /dev/sdf: Device or resource busy
mdadm: cannot open device /dev/sde5: Device or resource busy
mdadm: Cannot assemble mbr metadata on /dev/sde2
mdadm: no recogniseable superblock on /dev/sde1
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: cannot open device /dev/loop0: Device or resource busy
mdadm: /dev/sdd2 is identified as a member of /dev/md1, slot 2.
mdadm: /dev/sdc2 is identified as a member of /dev/md1, slot 4.
mdadm: /dev/sdb2 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sda2 is identified as a member of /dev/md1, slot 0.
mdadm: ignoring /dev/sda2 as it reports /dev/sdc2 as failed
mdadm: ignoring /dev/sdb2 as it reports /dev/sdc2 as failed
mdadm: no uptodate device for slot 0 of /dev/md1
mdadm: no uptodate device for slot 1 of /dev/md1
mdadm: added /dev/sdd2 to /dev/md1 as 2
mdadm: added /dev/sdc2 to /dev/md1 as 4
mdadm: /dev/md1 assembled from 0 drives and 1 spare - not enough to start the array.


```

```
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x56b24e09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     3919859     1959898+  fd  Linux raid autodetect
/dev/sda2         3919860  1953520064   974800102+  fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6caef167

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     3919859     1959898+  fd  Linux raid autodetect
/dev/sdb2         3919860  1953520064   974800102+  fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x634f8788

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     3919859     1959898+  fd  Linux raid autodetect
/dev/sdc2         3919860  1953520064   974800102+  fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8563194

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63     3919859     1959898+  fd  Linux raid autodetect
/dev/sdd2         3919860  1953520064   974800102+  fd  Linux raid autodetect

Disk /dev/sde: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00069bd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048    69797887    34897920   83  Linux
/dev/sde2        69799934    78163967     4182017    5  Extended
/dev/sde5        69799936    78163967     4182016   82  Linux swap / Solaris

Disk /dev/sdf: 3909 MB, 3909091328 bytes
102 heads, 38 sectors/track, 1969 cylinders, total 7634944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xee076347

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *        8064     7634943     3813440    b  W95 FAT32


```


do i have to use the last resort to create raid with assume clean option?

---

### Post by gareth6 on 2014-03-13
I had just removed one of the unused hard disk that does not belong to the array.
now it can add 1 more drive to array.

```
root@ubuntu:/home/ubuntu# mdadm --stop /dev/md1
mdadm: stopped /dev/md1
root@ubuntu:/home/ubuntu# mdadm --assemble --scan -v
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sdb2 has wrong uuid.
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdd2 has wrong uuid.
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: /dev/sdc2 has wrong uuid.
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: cannot open device /dev/loop0: Device or resource busy
mdadm: looking for devices for /dev/md1
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: cannot open device /dev/loop0: Device or resource busy
mdadm: /dev/sdb2 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sdd2 is identified as a member of /dev/md1, slot 2.
mdadm: /dev/sdc2 is identified as a member of /dev/md1, slot 4.
mdadm: /dev/sda2 is identified as a member of /dev/md1, slot 0.
mdadm: ignoring /dev/sda2 as it reports /dev/sdb2 as failed
mdadm: no uptodate device for slot 0 of /dev/md1
mdadm: added /dev/sdd2 to /dev/md1 as 2
mdadm: added /dev/sdc2 to /dev/md1 as 4
mdadm: added /dev/sdb2 to /dev/md1 as 1
mdadm: /dev/md1 assembled from 1 drive and 1 spare - not enough to start the array.



```

---

### Post by gareth6 on 2014-03-13
using force
```
root@ubuntu:/home/ubuntu# mdadm --assemble --force /dev/md1 /dev/sd[abcd]1
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has no superblock - assembly aborted
root@ubuntu:/home/ubuntu# mdadm --assemble --force /dev/md1 /dev/sd[abcd]2
mdadm: ignoring /dev/sda2 as it reports /dev/sdb2 as failed
mdadm: forcing event count in /dev/sdd2(2) from 3095571 upto 3095579
mdadm: clearing FAULTY flag for device 3 in /dev/md1 for /dev/sdd2
mdadm: Marking array /dev/md1 as 'clean'
mdadm: /dev/md1 has been started with 2 drives (out of 3) and 1 spare.
root@ubuntu:/home/ubuntu# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
md1 : active raid5 sdb2[1] sdc2[3](S) sdd2[4](F)
      1949600000 blocks level 5, 64k chunk, algorithm 2 [3/1] [_U_]
      
unused devices: <none>


```

```
root@ubuntu:/home/ubuntu# mdadm --detail /dev/md1
/dev/md1:
        Version : 0.90
  Creation Time : Fri Oct  1 08:56:24 2010
     Raid Level : raid5
     Array Size : 1949600000 (1859.28 GiB 1996.39 GB)
  Used Dev Size : 974800000 (929.64 GiB 998.20 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Thu Mar 13 08:56:47 2014
          State : clean, FAILED 
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 5b8e231f:cc0a4ab6:aebd925c:1f1edef4
         Events : 0.3095584

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       18        1      active sync   /dev/sdb2
       2       0        0        2      removed

       3       8       34        -      spare   /dev/sdc2
       4       8       50        -      faulty spare   /dev/sdd2


```

---

### Post by gareth6 on 2014-03-13
This time round i tried this
mdadm --assemble --scan --force -v
```
root@ubuntu:/home/ubuntu# mdadm --assemble --scan --force -v
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sdb2 has wrong uuid.
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdd2 has wrong uuid.
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: /dev/sdc2 has wrong uuid.
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: cannot open device /dev/loop0: Device or resource busy
mdadm: looking for devices for /dev/md1
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: cannot open device /dev/loop0: Device or resource busy
mdadm: /dev/sdb2 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sdd2 is identified as a member of /dev/md1, slot 2.
mdadm: /dev/sdc2 is identified as a member of /dev/md1, slot 3.
mdadm: /dev/sda2 is identified as a member of /dev/md1, slot 0.
mdadm: ignoring /dev/sda2 as it reports /dev/sdb2 as failed
mdadm: forcing event count in /dev/sdd2(2) from 3095580 upto 3095586
mdadm: clearing FAULTY flag for device 1 in /dev/md1 for /dev/sdd2
mdadm: Marking array /dev/md1 as 'clean'
mdadm: no uptodate device for slot 0 of /dev/md1
mdadm: added /dev/sdd2 to /dev/md1 as 2
mdadm: added /dev/sdc2 to /dev/md1 as 3
mdadm: added /dev/sdb2 to /dev/md1 as 1
mdadm: /dev/md1 has been started with 2 drives (out of 3) and 1 spare.
mdadm: looking for devices for /dev/md0
mdadm: no recogniseable superblock on /dev/md1
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: cannot open device /dev/sdb2: Device or resource busy
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sdd2: Device or resource busy
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: cannot open device /dev/sdc2: Device or resource busy
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: cannot open device /dev/loop0: Device or resource busy


```

now it tells me sda2 has wrong uuid
```
root@ubuntu:/home/ubuntu# mdadm --detail /dev/md1
/dev/md1:
        Version : 0.90
  Creation Time : Fri Oct  1 08:56:24 2010
     Raid Level : raid5
     Array Size : 1949600000 (1859.28 GiB 1996.39 GB)
  Used Dev Size : 974800000 (929.64 GiB 998.20 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Thu Mar 13 09:32:17 2014
          State : clean, FAILED 
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 5b8e231f:cc0a4ab6:aebd925c:1f1edef4
         Events : 0.3095591

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       18        1      active sync   /dev/sdb2
       2       0        0        2      removed

       3       8       34        -      spare   /dev/sdc2
       4       8       50        -      faulty spare   /dev/sdd2


```

---

