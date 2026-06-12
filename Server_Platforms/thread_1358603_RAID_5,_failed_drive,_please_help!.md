---
title: "RAID 5, failed drive, please help!"
date: 2009-12-18
forum: Server Platforms
---

### Post by fearlsgroove on 2009-12-18
Running Jaunty Server ... I've got a RAID 5 array consisting of 4 drives, one of which suffered a hardware failure. In trying to disconnect drives to determine which device was actually failed by seeing when the SMART warning dropped off during BIOS, I apparently let it get far enough that the last 2 drives appear REMOVED to mdadm.  

All 4 drives are now currently functioning, although the failed drive is flaky. I've also got a new drive ready to replace it. However because both 3rd (failed drive) and 4th (otherwise fine) drive appear as Removed I can't mount the array. Re-adding teh drives as so:
mdadm /dev/md0 -a /dev/sdc

caused them to show up as spares rather than as the original drives that they were.

so based on this thread: [http://osdir.com/ml/linux-raid/2009-06/msg00017.html](http://osdir.com/ml/linux-raid/2009-06/msg00017.html)

I'm attempting to re-create the array metadata with --assume-clean. My issue now is that I can't create a new array because /dev/sdc1 and /dev/sdd1 don't appear! They do show up in fdisk, so I believe the paritition tables are ok.

Here's the interesting bits:
```
$ sudo mdadm --misc -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 96b2a1f9:b696b022:e104bc29:f03ad111
  Creation Time : Sat Jun 13 08:57:26 2009
     Raid Level : raid5
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 2930279424 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 2
Preferred Minor : 0

    Update Time : Fri Dec 18 14:48:59 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 9753c5f8 - correct
         Events : 257017

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
```

```
$ sudo fdisk -l /dev/sdc

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000af453

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121601   976760001   fd  Linux raid autodetect
```

```
$ ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 2009-12-18 14:56 /dev/sda
brw-rw---- 1 root disk 8,  1 2009-12-18 14:56 /dev/sda1
brw-rw---- 1 root disk 8, 16 2009-12-18 14:56 /dev/sdb
brw-rw---- 1 root disk 8, 17 2009-12-18 14:56 /dev/sdb1
brw-rw---- 1 root disk 8, 32 2009-12-18 14:56 /dev/sdc
brw-rw---- 1 root disk 8, 48 2009-12-18 14:56 /dev/sdd
brw-rw---- 1 root disk 8, 64 2009-12-18 14:56 /dev/sde
brw-rw---- 1 root disk 8, 65 2009-12-18 14:58 /dev/sde1
brw-rw---- 1 root disk 8, 66 2009-12-18 14:56 /dev/sde2
```

And here's the command I'd like to run to re-create the array metadata:

```
sudo mdadm --create /dev/md0 --assume-clean --level=5 --chunk=256 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
```

How can I get the partitions on sdc and sdd to be "mounted", so that I can run the mdadm --create command? Is there a better way to to re-add the drives to the array without recreating the array metadata?

Thanks in advance, I REALLLY need to recover this array!

---

### Post by fearlsgroove on 2009-12-18
OK I managed to solve it (I think!). The sdc1 and sdd1 appeared after a reboot, then I had to stop the existing array with:

sudo mdadm --stop /dev/md0

and I was able to recreate the array and mount the LVM volumes that were contained on the array. Currently preparing to swap out the failing drive. hooray! now for a complete backup ...

---

### Post by fearlsgroove on 2009-12-18
Apparently it's not completely solved ... After a clean reboot, it comes up with only sdc1 and sdd1 in some kind of busted array:

```
$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd[5](S) sdc[4](S)
      1953524736 blocks
       
unused devices: <none>
```

Obviously md0 shows as inactive here. I can't recreate they array again at this point:

```
$ sudo mdadm --create /dev/md0 --assume-clean --level=5 --chunk=256 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: /dev/sda1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Fri Dec 18 16:50:14 2009
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Fri Dec 18 16:50:14 2009
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: Cannot open /dev/sdd1: Device or resource busy
mdadm: create aborted
```

however I can --assemble like so:
```
$ sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: /dev/md0 has been started with 4 drives.
```

... and mdstat looks as it should:
```
$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      2930279424 blocks level 5, 256k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>
```

Alternatively, after a clean reboot I can --stop and then --create:
```
$ sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0
$ sudo mdadm --create /dev/md0 --assume-clean --level=5 --chunk=256 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: /dev/sda1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Fri Dec 18 16:50:14 2009
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Fri Dec 18 16:50:14 2009
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Fri Dec 18 16:50:14 2009
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Fri Dec 18 16:50:14 2009
Continue creating array? y
mdadm: array /dev/md0 started.
```

However this also doesn't "Stick" after a reboot. From where is it creating this incorrect array of sdc and sdd? How can I get the proper array to persist across reboots? Please help!

---

### Post by fearlsgroove on 2009-12-18
Managed to find this thread:
[http://ubuntuforums.org/showthread.php?t=1101748](http://ubuntuforums.org/showthread.php?t=1101748)

which suggested this:

> A suggestion: first re-name or delete the /etc/mdadm/mdadm.conf file, remove (purge) mdadm from the system. Then reboot, re-install mdadm and see if we can assemble the array:

I didn't have to reassemble the array, after doing this it properly resurrected the array. I'm now getting ready to rebuild the array.

---

### Post by fearlsgroove on 2009-12-18
Continuing the conversation I've had with myself ..

I was wrong it still isn't properly restoring the arrays on reboot -- I clearly don't understand some aspects of how this is supposed to work. It's reading configuration by scanning the existing disks and I've thoroughly fouled that. Can someone PLEASE tell me how to clean up the mess I've made??!

I'm thinking this will help:
```
$ sudo mdadm -vv --examine --scan
mdadm: No md superblock detected on /dev/block/252:6.
mdadm: No md superblock detected on /dev/block/252:5.
mdadm: No md superblock detected on /dev/block/252:4.
mdadm: No md superblock detected on /dev/block/252:3.
mdadm: No md superblock detected on /dev/block/252:2.
mdadm: No md superblock detected on /dev/block/252:1.
mdadm: No md superblock detected on /dev/block/252:0.
mdadm: No md superblock detected on /dev/block/9:0.
mdadm: No md superblock detected on /dev/sde2.
mdadm: No md superblock detected on /dev/sde1.
mdadm: No md superblock detected on /dev/sde.
mdadm: No md superblock detected on /dev/sdd.
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 90795537:5f1ab955:32bb33b1:ae294b6e (local to host xen)
  Creation Time : Fri Dec 18 19:26:58 2009
     Raid Level : raid5
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 2930279424 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Dec 18 19:26:58 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 4a38455d - correct
         Events : 1

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 96b2a1f9:b696b022:e104bc29:f03ad111
  Creation Time : Sat Jun 13 08:57:26 2009
     Raid Level : raid5
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 2930279424 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Dec 18 04:56:40 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 975727a7 - correct
         Events : 257014

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     4       8       32       -1      spare   /dev/sdc

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 90795537:5f1ab955:32bb33b1:ae294b6e (local to host xen)
  Creation Time : Fri Dec 18 19:26:58 2009
     Raid Level : raid5
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 2930279424 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Dec 18 19:26:58 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 4a38454b - correct
         Events : 1

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty
mdadm: No md superblock detected on /dev/sdb.
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 90795537:5f1ab955:32bb33b1:ae294b6e (local to host xen)
  Creation Time : Fri Dec 18 19:26:58 2009
     Raid Level : raid5
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 2930279424 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Dec 18 19:26:58 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 4a384539 - correct
         Events : 1

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty
mdadm: No md superblock detected on /dev/sda.
```

How do i clear out teh arrays that I don't want from the disks? How come there appears to be superblocks on both sdx and sdx1 in some cases?

---

