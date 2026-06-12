---
title: "RAID6 fails to re-assemble after restart (left with spare device in /dev/md_dX)"
date: 2011-04-01
forum: Server Platforms
---

### Post by fermulator on 2011-04-01
As per, [http://ubuntuforums.org/showthread.php?t=1715955](http://ubuntuforums.org/showthread.php?t=1715955), I built a RAID6 array. yay.  In the end it completed.
```
fermulator@fermmy-server:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2000 : active raid6 sdo1[3] sdn1[2] sdm1[1] sdl1[0]
      3907026944 blocks level 6, 64k chunk, algorithm 2 [4/4] [UUUU]

```

To test stability, I rebooted the system, but on reboot, the array wasn't assembled correctly.  Basically it had one device in "md_d2000", as a spare.  So I stopped that device with 
```
sudo mdadm --stop /dev/md_d2000
```

The superblocks looked good ...
```
fermulator@fermmy-server:~$ sudo mdadm -E /dev/sd[lmno]
/dev/sdl:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 980a80e6:69d090ce:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Fri Apr  1 19:32:57 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2000

    Update Time : Fri Apr  1 19:32:57 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d3c368b - correct
         Events : 1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8      177        0      active sync   /dev/sdl1

   0     0       8      177        0      active sync   /dev/sdl1
   1     1       8      193        1      active sync   /dev/sdm1
   2     2       8      209        2      active sync   /dev/sdn1
   3     3       8      225        3      active sync   /dev/sdo1
/dev/sdm:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 980a80e6:69d090ce:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Fri Apr  1 19:32:57 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2000

    Update Time : Fri Apr  1 19:32:57 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d3c369d - correct
         Events : 1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8      193        1      active sync   /dev/sdm1

   0     0       8      177        0      active sync   /dev/sdl1
   1     1       8      193        1      active sync   /dev/sdm1
   2     2       8      209        2      active sync   /dev/sdn1
   3     3       8      225        3      active sync   /dev/sdo1
/dev/sdn:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 980a80e6:69d090ce:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Fri Apr  1 19:32:57 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2000

    Update Time : Fri Apr  1 19:32:57 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d3c36af - correct
         Events : 1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8      209        2      active sync   /dev/sdn1

   0     0       8      177        0      active sync   /dev/sdl1
   1     1       8      193        1      active sync   /dev/sdm1
   2     2       8      209        2      active sync   /dev/sdn1
   3     3       8      225        3      active sync   /dev/sdo1
/dev/sdo:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 980a80e6:69d090ce:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Fri Apr  1 19:32:57 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2000

    Update Time : Fri Apr  1 19:32:57 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d3c36c1 - correct
         Events : 1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8      225        3      active sync   /dev/sdo1

   0     0       8      177        0      active sync   /dev/sdl1
   1     1       8      193        1      active sync   /dev/sdm1
   2     2       8      209        2      active sync   /dev/sdn1
   3     3       8      225        3      active sync   /dev/sdo1

```

If I tried to recreate with "assume-clean", it seemed to be OK:
```
sudo mdadm --create --verbose /dev/md2000 --level=6 --raid-devices=4 --assume-clean /dev/sdl1 /dev/sdm1 /dev/sdn1 /dev/sdo1
```
However, on a reboot, the same problem would happen.

Then I tried to re-assemble the array using the UUIDs in the superblocks:
```
sudo mdadm --assemble /dev/md2000 --uuid=980a80e6:69d090ce:01f5a1db:50a22640
```
however, I got some odd error like:
> mdadm: appear to have very similar superblocks /dev/sdo /dev/sdo1

Luckily, I don't have any important data on the array yet ... so I zero'd the superblocks on all devices, deleted the partitions, and started over .. here I go again:
```
md2000 : active raid6 sdo1[3] sdn1[2] sdm1[1] sdl1[0]
      3907026944 blocks level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  resync =  0.7% (14164844/1953513472) finish=313.7min speed=102999K/sec
```

Any idea what happened?  I hope after /this/ rebuild ... that I won't have the same quirky problem.

---

### Post by fermulator on 2011-04-02
OK so the build has completed.  Here is some information before I reboot.

```
fermulator@fermmy-server:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2000 : active raid6 sdo1[3] sdn1[2] sdm1[1] sdl1[0]
      3907026944 blocks level 6, 64k chunk, algorithm 2 [4/4] [UUUU]

```

```
fermulator@fermmy-server:~$ sudo mdadm --query --verbose --detail /dev/md2000
/dev/md2000:
        Version : 00.90
  Creation Time : Fri Apr  1 19:42:45 2011
     Raid Level : raid6
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2000
    Persistence : Superblock is persistent

    Update Time : Sat Apr  2 01:17:42 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 97cedb21:aa421a90:01f5a1db:50a22640 (local to host fermmy-server)
         Events : 0.37

    Number   Major   Minor   RaidDevice State
       0       8      177        0      active sync   /dev/sdl1
       1       8      193        1      active sync   /dev/sdm1
       2       8      209        2      active sync   /dev/sdn1
       3       8      225        3      active sync   /dev/sdo1

```

```
fermulator@fermmy-server:~$ sudo fdisk -ul /dev/sd[lmno]

Disk /dev/sdl: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c11e7bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdm: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x53ed25f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdn: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce514e52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdn1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdo: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13f4af7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdo1            2048  3907029167  1953513560   fd  Linux raid autodetect

```

```
fermulator@fermmy-server:~$ sudo mdadm -E /dev/sd[lmno]1
/dev/sdl1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 97cedb21:aa421a90:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Fri Apr  1 19:42:45 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2000

    Update Time : Sat Apr  2 01:17:42 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4d726dc4 - correct
         Events : 37

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8      177        0      active sync   /dev/sdl1

   0     0       8      177        0      active sync   /dev/sdl1
   1     1       8      193        1      active sync   /dev/sdm1
   2     2       8      209        2      active sync   /dev/sdn1
   3     3       8      225        3      active sync   /dev/sdo1
/dev/sdm1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 97cedb21:aa421a90:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Fri Apr  1 19:42:45 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2000

    Update Time : Sat Apr  2 01:17:42 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4d726dd6 - correct
         Events : 37

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8      193        1      active sync   /dev/sdm1

   0     0       8      177        0      active sync   /dev/sdl1
   1     1       8      193        1      active sync   /dev/sdm1
   2     2       8      209        2      active sync   /dev/sdn1
   3     3       8      225        3      active sync   /dev/sdo1
/dev/sdn1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 97cedb21:aa421a90:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Fri Apr  1 19:42:45 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2000

    Update Time : Sat Apr  2 01:17:42 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4d726de8 - correct
         Events : 37

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8      209        2      active sync   /dev/sdn1

   0     0       8      177        0      active sync   /dev/sdl1
   1     1       8      193        1      active sync   /dev/sdm1
   2     2       8      209        2      active sync   /dev/sdn1
   3     3       8      225        3      active sync   /dev/sdo1
/dev/sdo1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 97cedb21:aa421a90:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Fri Apr  1 19:42:45 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2000

    Update Time : Sat Apr  2 01:17:42 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4d726dfa - correct
         Events : 37

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8      225        3      active sync   /dev/sdo1

   0     0       8      177        0      active sync   /dev/sdl1
   1     1       8      193        1      active sync   /dev/sdm1
   2     2       8      209        2      active sync   /dev/sdn1
   3     3       8      225        3      active sync   /dev/sdo1

```

Is it expected that mdadm can read both the primary /dev/sdX, and the partition /dev/sdX1?

```
fermulator@fermmy-server:~$ sudo mdadm -E /dev/sd[lmno]
/dev/sdl:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 97cedb21:aa421a90:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Fri Apr  1 19:42:45 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2000

    Update Time : Sat Apr  2 01:17:42 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4d726dc4 - correct
         Events : 37

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8      177        0      active sync   /dev/sdl1

   0     0       8      177        0      active sync   /dev/sdl1
   1     1       8      193        1      active sync   /dev/sdm1
   2     2       8      209        2      active sync   /dev/sdn1
   3     3       8      225        3      active sync   /dev/sdo1
/dev/sdm:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 97cedb21:aa421a90:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Fri Apr  1 19:42:45 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2000

    Update Time : Sat Apr  2 01:17:42 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4d726dd6 - correct
         Events : 37

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8      193        1      active sync   /dev/sdm1

   0     0       8      177        0      active sync   /dev/sdl1
   1     1       8      193        1      active sync   /dev/sdm1
   2     2       8      209        2      active sync   /dev/sdn1
   3     3       8      225        3      active sync   /dev/sdo1
/dev/sdn:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 97cedb21:aa421a90:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Fri Apr  1 19:42:45 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2000

    Update Time : Sat Apr  2 01:17:42 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4d726de8 - correct
         Events : 37

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8      209        2      active sync   /dev/sdn1

   0     0       8      177        0      active sync   /dev/sdl1
   1     1       8      193        1      active sync   /dev/sdm1
   2     2       8      209        2      active sync   /dev/sdn1
   3     3       8      225        3      active sync   /dev/sdo1
/dev/sdo:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 97cedb21:aa421a90:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Fri Apr  1 19:42:45 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2000

    Update Time : Sat Apr  2 01:17:42 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4d726dfa - correct
         Events : 37

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8      225        3      active sync   /dev/sdo1

   0     0       8      177        0      active sync   /dev/sdl1
   1     1       8      193        1      active sync   /dev/sdm1
   2     2       8      209        2      active sync   /dev/sdn1
   3     3       8      225        3      active sync   /dev/sdo1

```

---

### Post by fermulator on 2011-04-02
Sigh; the same thing keeps happening.


```
fermulator@fermmy-server:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid1] [raid0] [raid6] [raid5] [raid4] [raid10] 
md_d2000 : inactive sdl[0](S)
      1953514496 blocks

```

```
fermulator@fermmy-server:~$ sudo mdadm --stop /dev/md_d2000
mdadm: stopped /dev/md_d2000

```

```
fermulator@fermmy-server:~$ sudo mdadm --assemble /dev/md2000 --uuid=ad68c2b0:b93159de:01f5a1db:50a22640 -v
mdadm: looking for devices for /dev/md2000
mdadm: /dev/sdo1 has wrong uuid.
mdadm: /dev/sdo has wrong uuid.
mdadm: /dev/sdn1 has wrong uuid.
mdadm: /dev/sdn has wrong uuid.
mdadm: /dev/sdm1 has wrong uuid.
mdadm: /dev/sdm has wrong uuid.
mdadm: /dev/sdl1 has wrong uuid.
mdadm: /dev/sdl has wrong uuid.
mdadm: no recogniseable superblock on /dev/block/9:250
mdadm: /dev/block/9:250 has wrong uuid.
mdadm: cannot open device /dev/block/9:1000: Device or resource busy
mdadm: /dev/block/9:1000 has wrong uuid.
mdadm: cannot open device /dev/sdh1: Device or resource busy
mdadm: /dev/sdh1 has wrong uuid.
mdadm: cannot open device /dev/sdh: Device or resource busy
mdadm: /dev/sdh has wrong uuid.
mdadm: cannot open device /dev/sdk1: Device or resource busy
mdadm: /dev/sdk1 has wrong uuid.
mdadm: cannot open device /dev/sdk: Device or resource busy
mdadm: /dev/sdk has wrong uuid.
mdadm: cannot open device /dev/sdj1: Device or resource busy
mdadm: /dev/sdj1 has wrong uuid.
mdadm: cannot open device /dev/sdj: Device or resource busy
mdadm: /dev/sdj has wrong uuid.
mdadm: cannot open device /dev/sdi1: Device or resource busy
mdadm: /dev/sdi1 has wrong uuid.
mdadm: cannot open device /dev/sdi: Device or resource busy
mdadm: /dev/sdi has wrong uuid.
mdadm: /dev/sdg1 has wrong uuid.
mdadm: no recogniseable superblock on /dev/sdg
mdadm: /dev/sdg has wrong uuid.
mdadm: cannot open device /dev/sdf3: Device or resource busy
mdadm: /dev/sdf3 has wrong uuid.
mdadm: cannot open device /dev/sdf2: Device or resource busy
mdadm: /dev/sdf2 has wrong uuid.
mdadm: cannot open device /dev/sdf1: Device or resource busy
mdadm: /dev/sdf1 has wrong uuid.
mdadm: cannot open device /dev/sdf: Device or resource busy
mdadm: /dev/sdf has wrong uuid.
mdadm: cannot open device /dev/block/9:1002: Device or resource busy
mdadm: /dev/block/9:1002 has wrong uuid.
mdadm: cannot open device /dev/root: Device or resource busy
mdadm: /dev/root has wrong uuid.
mdadm: cannot open device /dev/sde3: Device or resource busy
mdadm: /dev/sde3 has wrong uuid.
mdadm: cannot open device /dev/sde2: Device or resource busy
mdadm: /dev/sde2 has wrong uuid.
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: /dev/sde1 has wrong uuid.
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sde has wrong uuid.
mdadm: /dev/sdd1 has wrong uuid.
mdadm: no recogniseable superblock on /dev/sdd
mdadm: /dev/sdd has wrong uuid.
mdadm: cannot open device /dev/sdc3: Device or resource busy
mdadm: /dev/sdc3 has wrong uuid.
mdadm: no recogniseable superblock on /dev/sdc2
mdadm: /dev/sdc2 has wrong uuid.
mdadm: no recogniseable superblock on /dev/sdc1
mdadm: /dev/sdc1 has wrong uuid.
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdc has wrong uuid.
mdadm: /dev/sdb1 has wrong uuid.
mdadm: no recogniseable superblock on /dev/sdb
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.
mdadm: no devices found for /dev/md2000

```

That's rediculous; why does it claim that sd[lmno] have different UUIDs?  Clearly in the superblocks from the previous post, and even now, compared to the mdadm detail of /dev/md2000 ... the UUIDs match!

```
fermulator@fermmy-server:~$ sudo mdadm --create --verbose /dev/md2000 --level=6 --raid-devices=4 --assume-clean /dev/sdl1 /dev/sdm1 /dev/sdn1 /dev/sdo1 
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/sdl1 appears to contain an ext2fs file system
    size=-233537408K  mtime=Mon Mar 21 21:31:53 1977
mdadm: /dev/sdl1 appears to be part of a raid array:
    level=raid6 devices=4 ctime=Fri Apr  1 19:42:45 2011
mdadm: /dev/sdm1 appears to contain an ext2fs file system
    size=-387940352K  mtime=Thu Mar 31 13:30:01 2011
mdadm: /dev/sdm1 appears to be part of a raid array:
    level=raid6 devices=4 ctime=Fri Apr  1 19:42:45 2011
mdadm: /dev/sdn1 appears to be part of a raid array:
    level=raid6 devices=4 ctime=Fri Apr  1 19:42:45 2011
mdadm: /dev/sdo1 appears to contain an ext2fs file system
    size=-408911808K  mtime=Mon Apr  3 23:12:25 2028
mdadm: /dev/sdo1 appears to be part of a raid array:
    level=raid6 devices=4 ctime=Fri Apr  1 19:42:45 2011
mdadm: size set to 1953513472K
Continue creating array? y
mdadm: array /dev/md2000 started.

```

```
fermulator@fermmy-server:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid1] [raid0] [raid6] [raid5] [raid4] [raid10] 
md2000 : active raid6 sdo1[3] sdn1[2] sdm1[1] sdl1[0]
      3907026944 blocks level 6, 64k chunk, algorithm 2 [4/4] [UUUU]

```

My mdadm.conf...

```
fermulator@fermmy-server:/media/arrays$ cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md1000 level=raid5 num-devices=4 UUID=209f0e99:53aa0416:01f5a1db:50a22640
ARRAY /dev/md1001 level=raid1 num-devices=2 UUID=a47de71c:3f2175fc:c28a4732:61396174
ARRAY /dev/md1002 level=raid1 num-devices=2 UUID=183d454b:79f57d43:13955f54:d42ead5c
ARRAY /dev/md250 level=raid1 num-devices=2 UUID=d25f3858:79bec3f1:01f5a1db:50a22640
ARRAY /dev/md2000 level=raid6 num-devices=4 UUID=5a3c624d:243fc226:01f5a1db:50a22640

# This file was auto-generated on Sun, 27 Mar 2011 10:43:22 -0400
# by mkconf $Id$

```

I scheduled a sync_check operation just to be sure....
```
fermulator@fermmy-server:~$ cat /sys/block/md2000/md/sync_action
check

```

Now it's re-syncing /again/....
```
fermulator@fermmy-server:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid1] [raid0] [raid6] [raid5] [raid4] [raid10] 
md2000 : active raid6 sdo1[3] sdn1[2] sdm1[1] sdl1[0]
      3907026944 blocks level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  check =  0.2% (5074500/1953513472) finish=366.6min speed=88565K/sec

```

Any idea what's going on here?  Why, after each reboot, do I have to re-assemble the array?

---

### Post by fermulator on 2011-04-02
OK so I have realized what the issue was.  The UUID in /etc/mdadm/mdadm.conf was wrong!  ugh.

After fixing it:
```
fermulator@fermmy-server:~$ cat /etc/mdadm/mdadm.conf | grep md2000
ARRAY /dev/md2000 level=raid6 num-devices=4 UUID=97cedb21:aa421a90:01f5a1db:50a22640

```

and rebooting, now the array auto-re-assembles (yay).
/except/ for one thing ... it's called "/dev/md_d2000" instead of "/dev/md2000"

---

### Post by fermulator on 2011-04-02
ah-ah;  solved.

Had to do:
```
sudo mdadm --examine --scan --config=mdadm.conf
```
, and examine the output for /etc/mdadm/mdadm.conf.

(apparently the UUID in mdadm.conf isn't exactly as shown in the superblocks...)

---

