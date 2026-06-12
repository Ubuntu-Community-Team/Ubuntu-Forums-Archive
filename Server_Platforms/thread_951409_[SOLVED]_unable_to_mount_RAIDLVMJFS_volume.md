---
title: "[SOLVED] unable to mount RAID/LVM/JFS volume"
date: 2008-10-18
forum: Server Platforms
---

### Post by NarsilAnduril on 2008-10-18
Hi,

Bad news, my RAID volumes aren't up anymore (after sever crash).

My status : Running Hardy server i386, mdadm RAID5 with 3 LVM on it, one 100Gb ext3 and two 500Gb JFS. After crash, the JFS volumes don't mount anymore but the ext3 does.

First mystery : two of the four RAID's HD (sda to d) aren't showing a valid partition table, but the RAID is up.

```
diego@pinguin:/mnt/movies$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c16d87a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a0ce5d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00100000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x560a3dac

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/md0: 1500.3 GB, 1500323119104 bytes
255 heads, 63 sectors/track, 182403 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c16d87a

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1       60801   488384001   fd  Linux raid autodetect

```

```
diego@pinguin:/mnt/movies$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Sep 25 22:27:26 2008
     Raid Level : raid5
     Array Size : 1465159296 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488386432 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Oct 18 10:16:41 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : ddd87174:a7a0d3b0:a499cc75:bbcf0225 (local to host pinguin)
         Events : 0.32

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd

```

Now, let's go further with the LVM' physical volume :

```
diego@pinguin:/mnt/movies$ sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/md0
  VG Name               RAID5
  PV Size               1.36 TB / not usable 35.81 MB
  Allocatable           yes 
  PE Size (KByte)       65536
  Total PE              22356
  Free PE               4756
  Allocated PE          17600
  PV UUID               MskkDk-uTFp-b3m1-B9YX-MDzL-MUMN-9xqVn6

```

```
diego@pinguin:/mnt/movies$ sudo pvscan
  PV /dev/md0   VG RAID5   lvm2 [1.36 TB / 297.25 GB free]
  Total: 1 [1.36 TB] / in use: 1 [1.36 TB] / in no VG: 0 [0   ]

```

And the volume group (only one) :

```
diego@pinguin:/mnt/movies$ sudo vgdisplay
  --- Volume group ---
  VG Name               RAID5
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  5
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                3
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               1.36 TB
  PE Size               64.00 MB
  Total PE              22356
  Alloc PE / Size       17600 / 1.07 TB
  Free  PE / Size       4756 / 297.25 GB
  VG UUID               gG0WR7-Coim-7I1m-S8s5-WvmU-ze3v-QcM78y

```

```
diego@pinguin:/mnt/movies$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "RAID5" using metadata type lvm2

```

And finally, logical volumes :

```
diego@pinguin:/mnt/movies$ sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/RAID5/records
  VG Name                RAID5
  LV UUID                Ne89KM-onY3-xGp0-j8og-aJuz-IDan-vvt4UL
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                500.00 GB
  Current LE             8000
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:0
   
  --- Logical volume ---
  LV Name                /dev/RAID5/movies
  VG Name                RAID5
  LV UUID                O5J3Xj-jo8Q-mZSo-C1Wu-wNQb-rnZs-u7NZZU
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                500.00 GB
  Current LE             8000
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:1
   
  --- Logical volume ---
  LV Name                /dev/RAID5/downloads
  VG Name                RAID5
  LV UUID                SwBfwn-NGP9-McFi-oyqT-Hpyb-eCvu-93KlXG
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                100.00 GB
  Current LE             1600
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:2

```

```
diego@pinguin:/mnt/movies$ sudo lvscan
  ACTIVE            '/dev/RAID5/records' [500.00 GB] inherit
  ACTIVE            '/dev/RAID5/movies' [500.00 GB] inherit
  ACTIVE            '/dev/RAID5/downloads' [100.00 GB] inherit

```

In my point of view, everything's looking good except the partition table.

But now, if I try to mount the JFS volumes :

```
diego@pinguin:/mnt/movies$ sudo mount /dev/RAID5/records /mnt/records -t jfs
mount: wrong fs type, bad option, bad superblock on /dev/mapper/RAID5-records,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

```
diego@pinguin:/mnt/movies$ sudo mount /dev/RAID5/movies /mnt/movies -t jfsmount: wrong fs type, bad option, bad superblock on /dev/mapper/RAID5-movies,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

But the ext3 one works :

```
diego@pinguin:/mnt/movies$ sudo mount /dev/RAID5/downloads /mnt/downloads -t ext3
diego@pinguin:/mnt/movies$ 
```

Help would be very welcome !

Thatks

Diego

---

### Post by promodus on 2008-10-18
I'm thinking create primary partitions, type fd on /dev/sdc and /dev/sdd

---

### Post by NarsilAnduril on 2008-10-18
Well, I have a lot of stuff on those disks .. I would prefer a non destructive approach !

And, remember, the ext3 volume on the same RAID(LVM is working !

---

### Post by NarsilAnduril on 2008-10-18
Did it, didn't change anything

```
diego@pinguin:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c16d87a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a0ce5d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd28fd79

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19142580

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/md0: 1500.3 GB, 1500323119104 bytes
255 heads, 63 sectors/track, 182403 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c16d87a

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1       60801   488384001   fd  Linux raid autodetect

```

---

### Post by NarsilAnduril on 2008-10-18
Ok, solved thanks to journaling :

```
diego@pinguin:/mnt/downloads/torrent/done$ sudo fsck.jfs -v /dev/RAID5/movies
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 10/18/2008 12.50.46
Using default parameter: -p
The current device is:  /dev/RAID5/movies
Open(...READ/WRITE EXCLUSIVE...) returned rc = 0
Primary superblock is valid.
The type of file system for the device is JFS.
Block size in bytes:  4096
Filesystem size in blocks:  131072000
**Phase 0 - Replay Journal Log
LOGREDO:  Allocating for ReDoPage:  (d) 4096 bytes
LOGREDO:  Allocating for NoDoFile:  (d) 4096 bytes
LOGREDO:  Allocating for BMap:  (d) 280880 bytes
LOGREDO:  Allocating for IMap:  (d) 16480 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Log record for Volume Mount at:    0x0cd4748
LOGREDO:  Log record for Sync Point at:    0x0cd4724
LOGREDO:  Beginning to update the Inode Allocation Map.
LOGREDO:  Done updating the Inode Allocation Map.
LOGREDO:  Beginning to update the Block Map.
LOGREDO:  Done updating the Block Map.
LOGREDO:  End of log found at logend = 0x0ce0f78
LOGREDO:  Synch point record number:  0x0cd4724
LOGREDO:  Synch point record address:  0x0cd4724
LOGREDO:  Number of log records:    (d) 490
LOGREDO:  Number of Do blocks:    (d) 10
LOGREDO:  Number of NoDo blocks:    (d) 3
logredo returned rc = 0
Filesystem is clean.
All observed inconsistencies have been repaired.
Filesystem has been marked clean.
**** Filesystem was modified. ****
processing terminated:  10/18/2008 12:50:51  with return code: 0  exit code: 0.

```

```
diego@pinguin:/mnt/downloads/torrent/done$ sudo fsck.jfs -v /dev/RAID5/records
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 10/18/2008 12.51.35
Using default parameter: -p
The current device is:  /dev/RAID5/records
Open(...READ/WRITE EXCLUSIVE...) returned rc = 0
Primary superblock is valid.
The type of file system for the device is JFS.
Block size in bytes:  4096
Filesystem size in blocks:  131072000
**Phase 0 - Replay Journal Log
LOGREDO:  Allocating for ReDoPage:  (d) 4096 bytes
LOGREDO:  Allocating for NoDoFile:  (d) 4096 bytes
LOGREDO:  Allocating for BMap:  (d) 280880 bytes
LOGREDO:  Allocating for IMap:  (d) 16752 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Log record for Sync Point at:    0x06c640
LOGREDO:  Beginning to update the Inode Allocation Map.
LOGREDO:  Done updating the Inode Allocation Map.
LOGREDO:  Beginning to update the Block Map.
LOGREDO:  Done updating the Block Map.
LOGREDO:  End of log found at logend = 0x0929b0
LOGREDO:  Synch point record number:  0x06c640
LOGREDO:  Synch point record address:  0x0678d4
LOGREDO:  Number of log records:    (d) 1779
LOGREDO:  Number of Do blocks:    (d) 5
LOGREDO:  Number of NoDo blocks:    (d) 0
logredo returned rc = 0
Filesystem is clean.
All observed inconsistencies have been repaired.
Filesystem has been marked clean.
**** Filesystem was modified. ****
processing terminated:  10/18/2008 12:51:40  with return code: 0  exit code: 0.

```

Hope this will help someone.

Pending questions : why did the JFS filesystem corrupt ? why did my system crash ?

Mystery still here : after rebuild, sdc and sdd still don't show valid partition table :

```
diego@pinguin:~$ sudo fdisk -l
[sudo] password for diego: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c16d87a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a0ce5d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00100000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x560a3dac

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/md0: 1500.3 GB, 1500323119104 bytes
255 heads, 63 sectors/track, 182403 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c16d87a

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1       60801   488384001   fd  Linux raid autodetect

```

---

### Post by promodus on 2008-10-18
Can you please post the output from:
```
cat /etc/mdadm/mdadm.conf 
```

---

### Post by NarsilAnduril on 2008-10-18
Here we are

```
diego@pinguin:~$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sd*

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR my@fakeemail.com

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=ddd87174:a7a0d3b0:a499cc75:bbcf0225

# This file was auto-generated on Sun, 28 Sep 2008 20:11:12 +0200
# by mkconf $Id$

```

---

### Post by jerome1232 on 2008-10-18
I was about to say jfs won't mount until the journal get's replayed, if I ever have a crash I have to fsck any jfs volumes.

---

### Post by promodus on 2008-10-18
First rule of RAID club:
RAID is no substitute for backups.
User discretion is advised.

I don't understand how your RAID is being built using partitions from 2 drives, then raw devices from 2 others.

Sometimes a RAID 5 can function on 2 drives. I wouldn't use it for long as you are operating without parity.

one suggestion, if you're using this array, install the sysstat package.
Use iostat and watch your drives... are they being used.

---

### Post by NarsilAnduril on 2008-10-19
You're absolutely right, but look at this :

```
diego@pinguin:/mnt/movies$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Sep 25 22:27:26 2008
     Raid Level : raid5
     Array Size : 1465159296 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488386432 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Oct 18 10:16:41 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : ddd87174:a7a0d3b0:a499cc75:bbcf0225 (local to host pinguin)
         Events : 0.32

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd
```

Doesn't this mean all four devices are up ?

Anyway, iostat looks pretty good :

```
diego@pinguin:~$ iostat
Linux 2.6.24-19-server (pinguin) 	19. 10. 08

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.25    0.37    0.17    0.52    0.00   98.69

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               1.00        39.29        33.93    2966384    2561208
sdb               1.00        39.45        33.68    2977826    2542344
sdc               1.00        39.46        33.99    2978768    2565768
sdd               1.00        39.63        33.72    2991400    2545536
md0              27.71       139.97        81.69   10566834    6166648
dm-0             19.25        72.53        81.47    5475344    6150152
dm-1              2.28        18.24         0.01    1377312        584
dm-2              6.17        49.18         0.21    3712514      15912
sde               0.71        11.78        19.85     889253    1498721
```

Diego

---

### Post by promodus on 2008-10-19
Hmmm...
I'm starting to think that maybe the partition on the RAID SET shows up on the RAID members...

As you alternate blocks and parity of the RAID SET, the resulting last few drives no longer show partition information.

Its a guess.

---

### Post by NarsilAnduril on 2008-10-19
I've managed to have it all running correctly (all disks with valid partition table).

My fault (I believe) was to fdisk sdc and sdd without stopping mdadm.

With mdadm stopped, the partition tables created are persistent.

Thanks for your help promodus and jerome1232, I've learn a lot with this.

And of course, never forget to backup ! (even if it's sometimes hard when you have many Tb ;-))

Diego

---

