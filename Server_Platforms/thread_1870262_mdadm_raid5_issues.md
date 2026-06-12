---
title: "mdadm raid5 issues"
date: 2011-10-26
forum: Server Platforms
---

### Post by agibby5 on 2011-10-26
I'm not sure what happened, but my raid5 array got into a weird state. Maybe it was a recent kernel upgrade.  It's been so long since I've setup my raid5 and I'm not having any luck here. I'm on 10.04 server edition.

I had a raid5 setup with /dev/sdb, /dev/sdc, /dev/sdd assembled to /dev/md0.

However, here's what it currently looks like:
```
cat /proc/mdstat
md0 : inactive sdb[0](S) sdd[2](S) sdc[1](S)
      5860543488 blocks
       
unused devices: <none>

```

```
sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb missing missing
mdadm: /dev/sdb appears to contain an ext2fs file system
    size=-387938304K  mtime=Wed Oct 26 09:00:54 2011
mdadm: /dev/sdb appears to be part of a raid array:
    level=raid5 devices=3 ctime=Mon Feb 21 18:21:10 2011
Continue creating array? no
mdadm: create aborted.
andy@server:~$ sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdc missing missing
mdadm: /dev/sdc appears to be part of a raid array:
    level=raid5 devices=3 ctime=Mon Feb 21 18:21:10 2011
Continue creating array? ^C
andy@server:~$ sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdd missing missing
mdadm: /dev/sdd appears to contain an ext2fs file system
    size=-408909760K  mtime=Mon Oct 30 03:56:20 2028
mdadm: /dev/sdd appears to be part of a raid array:
    level=raid5 devices=3 ctime=Mon Feb 21 18:21:10 2011
Continue creating array? n       
mdadm: create aborted.

```

```
sudo mdadm --assemble --verbose /dev/md0 /dev/sdb /dev/sdc /dev/sdd
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 2.
mdadm: added /dev/sdc to /dev/md0 as 1
mdadm: added /dev/sdd to /dev/md0 as 2
mdadm: added /dev/sdb to /dev/md0 as 0
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
```

```
sudo mdadm --examine /dev/sd[bcd] | egrep 'dev|Update|Role|State|Chunk Size'
/dev/sdb:
    Update Time : Wed Oct 26 18:01:34 2011
          State : clean
     Chunk Size : 64K
      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb
   0     0       8       16        0      active sync   /dev/sdb
/dev/sdc:
    Update Time : Wed Oct 26 17:00:37 2011
          State : clean
     Chunk Size : 64K
      Number   Major   Minor   RaidDevice State
this     1       8       32        1      active sync   /dev/sdc
   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
/dev/sdd:
    Update Time : Wed Oct 26 17:00:37 2011
          State : clean
     Chunk Size : 64K
      Number   Major   Minor   RaidDevice State
this     2       8       48        2      active sync   /dev/sdd
   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
```

```
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b190f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         262     2097152   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         262        9730    76052480   83  Linux

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

```


I was thinking of zeroing the superblock, recreating the array with 2 devices and a missing, then adding the third device, but I'm afraid that will destroy my data.  

Please let me know if you need anymore information. Thanks!

---

### Post by SeijiSensei on 2011-10-27
Use fdisk or gparted to create a single partition on each of the three component drives, then mark them as type "fd" (using fdisk's "t" command).  In the "mdadm --create" command, identify the components as /dev/sdb1, /dev/sdc1, and /dev/sdd1 rather than /dev/sdb, etc.  See if that helps.

---

### Post by rubylaser on 2011-10-27
I would like to see the full output of...
```
mdadm -E /dev/sd[bcd]
```
and
```
cat /etc/mdadm/mdadm.conf
```

As long as your events aren't totally screwed up, you should be able to stop /dev/md0, and force the array back together based on the above info.

---

### Post by agibby5 on 2011-10-27
> **SeijiSensei said:**
> Use fdisk or gparted to create a single partition on each of the three component drives, then mark them as type "fd" (using fdisk's "t" command).  In the "mdadm --create" command, identify the components as /dev/sdb1, /dev/sdc1, and /dev/sdd1 rather than /dev/sdb, etc.  See if that helps.

Wont that blow away all my data?




> **rubylaser said:**
> I would like to see the full output of...
```
mdadm -E /dev/sd[bcd]
```
and
```
cat /etc/mdadm/mdadm.conf
```

As long as your events aren't totally screwed up, you should be able to stop /dev/md0, and force the array back together based on the above info.

As requested:

```
sudo mdadm -E /dev/sd[bcd]
[sudo] password for andy: 
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 48f6580a:a1593327:01f9e43d:ac30fbff (local to host server)
  Creation Time : Mon Feb 21 18:21:10 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 3907028992 (3726.03 GiB 4000.80 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Wed Oct 26 18:01:34 2011
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 5222ac10 - correct
         Events : 6888

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb

   0     0       8       16        0      active sync   /dev/sdb
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 48f6580a:a1593327:01f9e43d:ac30fbff (local to host server)
  Creation Time : Mon Feb 21 18:21:10 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 3907028992 (3726.03 GiB 4000.80 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Wed Oct 26 17:00:37 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 52229dbd - correct
         Events : 6884

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       32        1      active sync   /dev/sdc

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 48f6580a:a1593327:01f9e43d:ac30fbff (local to host server)
  Creation Time : Mon Feb 21 18:21:10 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 3907028992 (3726.03 GiB 4000.80 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Wed Oct 26 17:00:37 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 52229dcf - correct
         Events : 6884

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       48        2      active sync   /dev/sdd

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd

```


```
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
MAILADDR xxxxxxxxxxxxxx

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=48f6580a:a1593327:01f9e43d:ac30fbff

# This file was auto-generated on Tue, 06 Sep 2011 17:01:31 -0400
# by mkconf $Id$

```

---

### Post by rubylaser on 2011-10-27
I wouldn't suggest adding a partition to your disks.  Just leave them as is.

Looks like /dev/sdc and /dev/sdd are in sync, so you'll want to stop your array.
```
mdadm --stop /dev/md0
```

Then, you can assemble the array with the two synced disks
```
mdadm --assemble --force /dev/md0 /dev/sd[cd]
```

Hopefully, the array will assemble (missing the one disk).  Verify you data is intact, and let them resync if necessary.  Once that's done, re-add /dev/sdb to the array, and it should resync.

---

### Post by agibby5 on 2011-10-27
> **rubylaser said:**
> I wouldn't suggest adding a partition to your disks.  Just leave them as is.

Looks like /dev/sdc and /dev/sdd are in sync, so you'll want to stop your array.
```
mdadm --stop /dev/md0
```

Then, you can assemble the array with the two synced disks
```
mdadm --assemble --force /dev/md0 /dev/sd[cd]
```

Hopefully, the array will assemble (missing the one disk).  Verify you data is intact, and let them resync if necessary.  Once that's done, re-add /dev/sdb to the array, and it should resync.

You're basically a lifesaver!  I forced the array like you said. It said the disks were in sync and it looked like the files were good.  So I added /dev/sdb and it's resyncing now!  Again, I appreciate this so much. I'm not sure how I got into this situation. The only thing I can think of was the kernel upgrade. Other than that, this server just shuts down and starts up at my specified intervals and serves as a file server.  But I was really worried about losing all my data!

---

### Post by rubylaser on 2011-10-27
No problem, glad to be of service :)  I understand how the fear of losing date can make one feel.  Please mark the thread as SOLVED up in the thread tools at the top.

---

### Post by agibby5 on 2011-10-28
I marked it SOLVED, but I perhaps should have waited until the sync finished up.  I guess something is wrong with one of the drives.  But I'm not sure how to read these mdadm reports.

```
sudo mdadm -E /dev/sd[bcd]
[sudo] password for andy: 
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 48f6580a:a1593327:01f9e43d:ac30fbff (local to host server)
  Creation Time : Mon Feb 21 18:21:10 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 3907028992 (3726.03 GiB 4000.80 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Oct 28 09:39:23 2011
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 5224dae4 - correct
         Events : 7084

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       16        3      spare   /dev/sdb

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8       16        3      spare   /dev/sdb
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 48f6580a:a1593327:01f9e43d:ac30fbff (local to host server)
  Creation Time : Mon Feb 21 18:21:10 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 3907028992 (3726.03 GiB 4000.80 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Oct 28 06:08:16 2011
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 5224a958 - correct
         Events : 7072

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       32        1      active sync   /dev/sdc

   0     0       0        0        0      removed
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8       16        3      spare   /dev/sdb
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 48f6580a:a1593327:01f9e43d:ac30fbff (local to host server)
  Creation Time : Mon Feb 21 18:21:10 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 3907028992 (3726.03 GiB 4000.80 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Oct 28 09:39:23 2011
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 5224db08 - correct
         Events : 7084

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       48        2      active sync   /dev/sdd

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8       16        3      spare   /dev/sdb

```

Is there something wrong with the raid setup now?  When looking at the information, it looks like /dev/sdc is absent now (before it was sdb).  Should I build the array with the other two? I'm not sure the rebuild succeeded or failed, as I let it go overnight and this is what I woke up to.

---

### Post by SeijiSensei on 2011-10-28
> **agibby5 said:**
> Wont that blow away all my data?

I didn't realize the array had data on it.  I thought you were building an array from scratch.

If I were you, I'd go buy a big external drive today and back up everything on the array.  It sounds like at least one of the drives has some hardware problems.  You don't want to be in the situation where only one of the three RAID 5 drives can function.  Been there, done that, never again.  Time to backup now.

---

### Post by rubylaser on 2011-10-28
Yes, drive b and d are in sync. Is the array mounted and are the files available?  If so, you need to get a backup now as SeijiSensei said.  I would run smartmontools against each disk and find the failing drive (should show up in dmesg too).

If your array isn't mounted or avialable, you'll want to stop /dev/md0 again, and force assemble with /dev/sdb and /dev/sdd as those two are in sync.

---

