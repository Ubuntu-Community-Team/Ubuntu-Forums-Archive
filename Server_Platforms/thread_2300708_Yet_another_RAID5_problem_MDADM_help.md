---
title: "Yet another RAID5 problem MDADM help"
date: 2015-10-28
forum: Server Platforms
---

### Post by Badger3x on 2015-10-28
Hi guys,

So I build a Ubuntu 14.04 RAID recovery box. I have a Thecus N5200 Pro NAS which uses linux to do its RAID.
It was configured as a 5 drive RAID5 array, but got its knickers in a knot whilst trying to rebuild after a disk problem.

Disks 0,1,2 and 4 are fine and still good RAID members. Disk 3 is faulty, though still spins up ok. Excessive reads then to upset it.

So I followed the instructions that a fellow thecus user wrote up:
[http://thecususergroup.proboards.com/thread/4156/recover-thecus-raid-pc](http://thecususergroup.proboards.com/thread/4156/recover-thecus-raid-pc)
[this is now an ancient and dead thread]

I got all the way to the end 
```
root@badger-System-Product-Name:/etc/lvm/backup# mount /dev/vg0/lv0 /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/mapper/vg0-lv0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
 but can not seem to mount the file system :(

syslog says:
```
Oct 28 12:02:07 badger-System-Product-Name kernel: [ 6811.527189] EXT4-fs (dm-1): mounting ext3 file system using the ext4 subsystem
Oct 28 12:02:07 badger-System-Product-Name kernel: [ 6811.618148] JBD2: no valid journal superblock found
Oct 28 12:02:07 badger-System-Product-Name kernel: [ 6811.618157] EXT4-fs (dm-1): error loading journal
```





Here is what I had done:
Check each disk with mdadm
```
root@badger-System-Product-Name:/home/badger# mdadm --examine /dev/sda2
/dev/sda2:
          Magic : a92b4efc
        Version : 0.90.02
           UUID : 83ecee4c:8aaa7ab7:66c53d63:cbfe4964
  Creation Time : Fri Aug 13 11:45:02 2010
     Raid Level : raid5
  Used Dev Size : 1951552000 (1861.15 GiB 1998.39 GB)
     Array Size : 7806208000 (7444.58 GiB 7993.56 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 126

    Update Time : Wed Oct 28 10:06:40 2015
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 1ce2675 - correct
         Events : 3035870

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       82        0      active sync   /dev/sdf2

   0     0       8       82        0      active sync   /dev/sdf2
   1     1       8       66        1      active sync   /dev/sde2
   2     2       8       50        2      active sync   /dev/sdd2
   3     3       0        0        3      faulty removed
   4     4       8       18        4      active sync   /dev/sdb2
root@badger-System-Product-Name:/home/badger# mdadm --examine /dev/sdb2
/dev/sdb2:
          Magic : a92b4efc
        Version : 0.90.02
           UUID : 83ecee4c:8aaa7ab7:66c53d63:cbfe4964
  Creation Time : Fri Aug 13 11:45:02 2010
     Raid Level : raid5
  Used Dev Size : 1951552000 (1861.15 GiB 1998.39 GB)
     Array Size : 7806208000 (7444.58 GiB 7993.56 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 126

    Update Time : Wed Oct 28 10:06:40 2015
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 1ce2667 - correct
         Events : 3035870

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       66        1      active sync   /dev/sde2

   0     0       8       82        0      active sync   /dev/sdf2
   1     1       8       66        1      active sync   /dev/sde2
   2     2       8       50        2      active sync   /dev/sdd2
   3     3       0        0        3      faulty removed
   4     4       8       18        4      active sync   /dev/sdb2
root@badger-System-Product-Name:/home/badger# mdadm --examine /dev/sdc2
/dev/sdc2:
          Magic : a92b4efc
        Version : 0.90.02
           UUID : 83ecee4c:8aaa7ab7:66c53d63:cbfe4964
  Creation Time : Fri Aug 13 11:45:02 2010
     Raid Level : raid5
  Used Dev Size : 1951552000 (1861.15 GiB 1998.39 GB)
     Array Size : 7806208000 (7444.58 GiB 7993.56 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 126

    Update Time : Wed Oct 28 10:06:40 2015
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 1ce2659 - correct
         Events : 3035870

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8       50        2      active sync   /dev/sdd2

   0     0       8       82        0      active sync   /dev/sdf2
   1     1       8       66        1      active sync   /dev/sde2
   2     2       8       50        2      active sync   /dev/sdd2
   3     3       0        0        3      faulty removed
   4     4       8       18        4      active sync   /dev/sdb2
root@badger-System-Product-Name:/home/badger# mdadm --examine /dev/sdd2
/dev/sdd2:
          Magic : a92b4efc
        Version : 0.90.02
           UUID : 83ecee4c:8aaa7ab7:66c53d63:cbfe4964
  Creation Time : Fri Aug 13 11:45:02 2010
     Raid Level : raid5
  Used Dev Size : 1951552000 (1861.15 GiB 1998.39 GB)
     Array Size : 7806208000 (7444.58 GiB 7993.56 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 1

    Update Time : Tue Oct  6 12:24:29 2015
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 1b11253 - correct
         Events : 3029375

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     3       8       50        3      active sync   /dev/sdd2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2
   2     2       8       34        2      active sync   /dev/sdc2
   3     3       8       50        3      active sync   /dev/sdd2
   4     4       0        0        4      faulty removed
   5     5       8       66        4      spare   /dev/sde2
root@badger-System-Product-Name:/home/badger# mdadm --examine /dev/sde2
/dev/sde2:
          Magic : a92b4efc
        Version : 0.90.02
           UUID : 83ecee4c:8aaa7ab7:66c53d63:cbfe4964
  Creation Time : Fri Aug 13 11:45:02 2010
     Raid Level : raid5
  Used Dev Size : 1951552000 (1861.15 GiB 1998.39 GB)
     Array Size : 7806208000 (7444.58 GiB 7993.56 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 126

    Update Time : Wed Oct 28 10:06:40 2015
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 1ce263d - correct
         Events : 3035870

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     4       8       18        4      active sync   /dev/sdb2

   0     0       8       82        0      active sync   /dev/sdf2
   1     1       8       66        1      active sync   /dev/sde2
   2     2       8       50        2      active sync   /dev/sdd2
   3     3       0        0        3      faulty removed
   4     4       8       18        4      active sync   /dev/sdb2
```

So disk 3 /sdd thinks it is part of the array still - but it is not. It also thinks there is a spare, but that is also not the case.
Disks 0,1,2,4 all seem to be ok but aware that disk 3 is not their friend anymore.



Next I had a look what sfdisk had to say:
```
root@badger-System-Product-Name:/home/badger# sfdisk -l /dev/sda

Disk /dev/sda: 243201 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+    243     244-   1959898+  fd  Linux RAID autodetect
/dev/sda2        244  243200  242957  1951552102+  fd  Linux RAID autodetect
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
root@badger-System-Product-Name:/home/badger# sfdisk -l /dev/sdb

Disk /dev/sdb: 243201 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0+    243     244-   1959898+  fd  Linux RAID autodetect
/dev/sdb2        244  243200  242957  1951552102+  fd  Linux RAID autodetect
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
root@badger-System-Product-Name:/home/badger# sfdisk -l /dev/sdc

Disk /dev/sdc: 243201 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdc1          0+    243     244-   1959898+  fd  Linux RAID autodetect
/dev/sdc2        244  243200  242957  1951552102+  fd  Linux RAID autodetect
/dev/sdc3          0       -       0          0    0  Empty
/dev/sdc4          0       -       0          0    0  Empty
root@badger-System-Product-Name:/home/badger# sfdisk -l /dev/sdd

Disk /dev/sdd: 243201 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdd1          0+    243     244-   1959898+  fd  Linux RAID autodetect
/dev/sdd2        244  243200  242957  1951552102+  fd  Linux RAID autodetect
/dev/sdd3          0       -       0          0    0  Empty
/dev/sdd4          0       -       0          0    0  Empty
root@badger-System-Product-Name:/home/badger# sfdisk -l /dev/sde

Disk /dev/sde: 243201 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sde1          0+    243     244-   1959898+  fd  Linux RAID autodetect
/dev/sde2        244  243200  242957  1951552102+  fd  Linux RAID autodetect
/dev/sde3          0       -       0          0    0  Empty
/dev/sde4          0       -       0          0    0  Empty
```

partition 2 on each disk is the RAID5 partition I am interested in...


Next I had a look with mdadm
```

root@badger-System-Product-Name:/home/badger# mdadm --examine --scan  /dev/sda1 /dev/sda2
ARRAY /dev/md126 UUID=83ecee4c:8aaa7ab7:66c53d63:cbfe4964
ARRAY /dev/md127 UUID=c4362a4a:8f88badf:b96da074:e7995510
root@badger-System-Product-Name:/home/badger# mdadm --examine --scan  /dev/sdb1 /dev/sdb2
ARRAY /dev/md126 UUID=83ecee4c:8aaa7ab7:66c53d63:cbfe4964
ARRAY /dev/md127 UUID=c4362a4a:8f88badf:b96da074:e7995510
root@badger-System-Product-Name:/home/badger# mdadm --examine --scan  /dev/sdc1 /dev/sdc2
ARRAY /dev/md126 UUID=83ecee4c:8aaa7ab7:66c53d63:cbfe4964
ARRAY /dev/md127 UUID=c4362a4a:8f88badf:b96da074:e7995510
root@badger-System-Product-Name:/home/badger# mdadm --examine --scan  /dev/sdd1 /dev/sdd2
ARRAY /dev/md1 UUID=83ecee4c:8aaa7ab7:66c53d63:cbfe4964
ARRAY /dev/md0 UUID=13a6b05d:2a3c5ba5:681ddb0f:bf32bd43
root@badger-System-Product-Name:/home/badger# mdadm --examine --scan  /dev/sde1 /dev/sde2
ARRAY /dev/md126 UUID=83ecee4c:8aaa7ab7:66c53d63:cbfe4964
ARRAY /dev/md127 UUID=c4362a4a:8f88badf:b96da074:e7995510

```

Disk 3 /sdd seems to think it belongs to a different raid group? md1 and md0?

Ok, next I looked at /proc/mdstat

```
root@badger-System-Product-Name:/home/badger# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md125 : active (auto-read-only) raid5 sdb2[1] sdc2[2] sda2[0] sde2[4]
      7806208000 blocks level 5, 256k chunk, algorithm 2 [5/4] [UUU_U]
      
md126 : inactive sdd1[3](S)
      1959808 blocks
       
md127 : active (auto-read-only) raid1 sdb1[1] sda1[0] sde1[3] sdc1[2]
      1959808 blocks [5/4] [UUUU_]

unused devices: <none>

```

Bit confused now. md125 is raid5??? Is that the one I want? md127 is raid1? not one I set up - possibly one the system
creates for itself om the Thecus NAS? Based on everything so far, I thought I want md126, but mdstat thinks it is borked?
Not sure what I am seeing.


Next I ran vgscan (following instructions from link I posted earlier)
```
root@badger-System-Product-Name:/home/badger# vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "vg0" using metadata type lvm2
root@badger-System-Product-Name:/home/badger# cd /etc/lvm/backup
root@badger-System-Product-Name:/etc/lvm/backup# vgcfgrestore -f vg0 vg0
  Restored volume group vg0
root@badger-System-Product-Name:/etc/lvm/backup# vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "vg0" using metadata type lvm2
root@badger-System-Product-Name:/etc/lvm/backup# pvscan
  PV /dev/md125   VG vg0   lvm2 [7.27 TiB / 592.00 MiB free]
  Total: 1 [7.27 TiB] / in use: 1 [7.27 TiB] / in no VG: 0 [0   ]
root@badger-System-Product-Name:/etc/lvm/backup# modprobe dm-mod
root@badger-System-Product-Name:/etc/lvm/backup# vgchange vg0 -a y
  2 logical volume(s) in volume group "vg0" now active
root@badger-System-Product-Name:/etc/lvm/backup# lvscan
  ACTIVE            '/dev/vg0/syslv' [1.00 GiB] inherit
  ACTIVE            '/dev/vg0/lv0' [7.27 TiB] inherit
root@badger-System-Product-Name:/etc/lvm/backup# mount /dev/vg0/lv0 /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/mapper/vg0-lv0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```


I have a feeling it has something to do with md125 vs md126. 

Thoughts appreciated.

---

### Post by darkod on 2015-10-28
It is weird when md devices change name on you but it shouldn't matter much for mdadm assemble because it looks for array members by uuid. Can you also post your mdadm.conf file?

The array is assembled with one member missing (the failed one). The lvm seems to activate correctly. Without trying to mount the lv, have you tried to do fsck on it? There could be few errors if second disk fails during rebuild. But in that case the array will fail and stop working. In your case it seems it assembles good. Were you doing some recovery after it failed during rebuild? That could provoke some corruption and could explain why the filesystem refuses to mount. I would run fsck on it.

---

### Post by Badger3x on 2015-10-28
> **darkod said:**
> It is weird when md devices change name on you but it shouldn't matter much for mdadm assemble because it looks for array members by uuid. Can you also post your mdadm.conf file?.


sure thing
```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Wed, 28 Oct 2015 08:00:09 +0800
# by mkconf $Id$



```

> **darkod said:**
> 
The array is assembled with one member missing (the failed one). The lvm seems to activate correctly. Without trying to mount the lv, have you tried to do fsck on it? There could be few errors if second disk fails during rebuild. But in that case the array will fail and stop working. In your case it seems it assembles good. Were you doing some recovery after it failed during rebuild? That could provoke some corruption and could explain why the filesystem refuses to mount. I would run fsck on it.

I have not attempted any recovery after the failed rebuild. It never mounted for me again in the Thecus.

To give you some additional history.
The Thecus NAS had smart errors 'current pending sectors' on disk 3 and disk4. 
Disk 3 had an error count of 6 errors and power on hours 7500.
Disk 4 had an error count of 1087 and power on hours of 260.
I had powered it down, removed disk 4, replaced with a brand new disk and booted. Defined NEW disk 4 as spare.
Allowed it to commence rebuilding to NEW disk 4.
After 30 mins or so Disk 3 dropped out of the array entirely.
I thought faulty power, so allowed it to proceed once more after a reboot.
Again, disk 3 drops out (looks like it is more f&&ked than previous disk4 was)

So i figured, ok, I still have disk 0,1,2 and 4 which work, lets put this combination in and
make a new spare for disk slot 3. Except it never saw the RAID config again.
Thus I am here.
I had not run an fsck on the system during the recovery process or after.

hope that helps give you and idea where i am at, now that I have brought i all over to my recovery box.

---

### Post by darkod on 2015-10-28
You might have bigger problems than you think. What you described is exactly the most critical moment of raid5, a second failure during rebuild. The problem is that unless the rebuild was completely done in the 30mins, which is unlikely, the new disk still hasn't got all the necessary data copied on it. So when another old disk fails, effectively you are left with 3 disks with correct data out of 5. Not with 4 good disks as you think. And of course a 5 member raid5 can't start with only 3 good members.

Now the only question is how close was the new disk to a full rebuild because the Events counters in the --examine actually don't look bad.

Can you tell which of the disks is the new one? sda,sde,etc?

Apart from that you can see in mdadm you have no ARRAY definitions so the system would not assemble any array on boot. I don't know if it's supposed to work like that if it assembles differently.

---

### Post by Badger3x on 2015-10-28
> **darkod said:**
> You might have bigger problems than you think. What you described is exactly the most critical moment of raid5, a second failure during rebuild. The problem is that unless the rebuild was completely done in the 30mins, which is unlikely, the new disk still hasn't got all the necessary data copied on it. So when another old disk fails, effectively you are left with 3 disks with correct data out of 5. Not with 4 good disks as you think. And of course a 5 member raid5 can't start with only 3 good members.

Now the only question is how close was the new disk to a full rebuild because the Events counters in the --examine actually don't look bad.

Can you tell which of the disks is the new one? sda,sde,etc?

Apart from that you can see in mdadm you have no ARRAY definitions so the system would not assemble any array on boot. I don't know if it's supposed to work like that if it assembles differently.

I am not using a half-rebuilt RAID disk member. none of what i am doing here involves the 'new disk' i mentioned to you in
the history. Disk 0,1,2 are in tact, disk 4 had manually been 'failed' by physically removing it. It had not actually failed in
the RAID set. Disk 3 is faulty and had failed out of the raid set during rebuild as you noted. However, going back to the state from before i attempted to rebuild, disk 0,1,2,and 4 have all the data needed to rebuild freshly now. (assuming no mechanical faliure on disk 4 during rebuild, like disk 3 had exhibited).

i am trying to get new raid set definitions set up here after transplanting the drives from my NAS to this linux recovery box.

Makes sense?

---

### Post by darkod on 2015-10-28
Yeah, it's getting clearer. Only issue might be that 0,1,2 might have changed a bit during the rebuild intent so they will not be in sync with 4. Making sense?

But looking at the --examine you posted in your first post, things look hopeful. In it you have partitions sda2-sde2. Comparing the Events counters and the UpdateTime, am I to assume that the four good disks from before the rebuild are sda2,sdb2,sdc2 and sde2?

In such case sdd2 is what? The slot 3 that failed during the rebuild?

And you still have the new disk you tried to rebuld with disconnected and put aside right?

---

### Post by Badger3x on 2015-10-28
> **darkod said:**
> Yeah, it's getting clearer. Only issue might be that 0,1,2 might have changed a bit during the rebuild intent so they will not be in sync with 4. Making sense?


indeed. Though they should not have been written to, if it was trying to rebuild another disk, no?

> **darkod said:**
> 
But looking at the --examine you posted in your first post, things look hopeful. In it you have partitions sda2-sde2. Comparing the Events counters and the UpdateTime, am I to assume that the four good disks from before the rebuild are sda2,sdb2,sdc2 and sde2?
That is correct sir.

> **darkod said:**
> 
In such case sdd2 is what? The slot 3 that failed during the rebuild?
sdd2 is the original slot3 disk that failed during the rebuild, yes.

And you still have the new disk you tried to rebuld with disconnected and put aside right?[/QUOTE]
I have, but for purposes of this exercise, I felt it was not needed (since it did not complete successfully) and has been placed
aside. It has no information of use for us does it (as it never became a proper RAID set member)?

---

### Post by darkod on 2015-10-28
Ok. Here is what I would do:
1. Keep the new disk aside. You are correct, it doesn't help right now.
2. Power down and remove sdd (the slot 3 failure). Since you know the disk is bad it can only do damage. It's out of sync with the others anyway.
3. After you boot again, check with cat /proc/mdstat that no array is running. There should be none since it's not configured to auto assemble.
4. At this point try the basic assemble with scan (the scan finds members automatically so no need to specify anything)
```
sudo mdadm --assemble --scan --verbose
```

Lets see how that goes.

---

### Post by Badger3x on 2015-10-28
> **darkod said:**
> Ok. Here is what I would do:
1. Keep the new disk aside. You are correct, it doesn't help right now.
2. Power down and remove sdd (the slot 3 failure). Since you know the disk is bad it can only do damage. It's out of sync with the others anyway.
3. After you boot again, check with cat /proc/mdstat that no array is running. There should be none since it's not configured to auto assemble.
4. At this point try the basic assemble with scan (the scan finds members automatically so no need to specify anything)
```
sudo mdadm --assemble --scan --verbose
```

Lets see how that goes.

so, did exactly as you proposed, steps 1, 2 and 3. and was surprised to see:

```
root@badger-System-Product-Name:/home/badger# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md126 : active (auto-read-only) raid5 sdb2[1] sdc2[2] sdd2[4] sda2[0]
      7806208000 blocks level 5, 256k chunk, algorithm 2 [5/4] [UUU_U]
      
md127 : active (auto-read-only) raid1 sdb1[1] sda1[0] sdd1[3] sdc1[2]
      1959808 blocks [5/4] [UUUU_]
      
unused devices: <none>


```
so it has picked up the RAID?

next step 4 (is superfluous?)
```
root@badger-System-Product-Name:/home/badger# mdadm --assemble --scan --verbose
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/sde4
mdadm: no recogniseable superblock on /dev/sde3
mdadm: no recogniseable superblock on /dev/sde2
mdadm: Cannot assemble mbr metadata on /dev/sde1
mdadm: Cannot assemble mbr metadata on /dev/sde
mdadm: no recogniseable superblock on /dev/dm-1
mdadm: no recogniseable superblock on /dev/dm-0
mdadm: no recogniseable superblock on /dev/md/125_0
mdadm: no recogniseable superblock on /dev/md/127_0
mdadm: /dev/sdd2 is busy - skipping
mdadm: /dev/sdd1 is busy - skipping
mdadm: Cannot assemble mbr metadata on /dev/sdd
mdadm: /dev/sdc2 is busy - skipping
mdadm: /dev/sdc1 is busy - skipping
mdadm: Cannot assemble mbr metadata on /dev/sdc
mdadm: /dev/sdb2 is busy - skipping
mdadm: /dev/sdb1 is busy - skipping
mdadm: Cannot assemble mbr metadata on /dev/sdb
mdadm: /dev/sda2 is busy - skipping
mdadm: /dev/sda1 is busy - skipping
mdadm: Cannot assemble mbr metadata on /dev/sda
mdadm: No arrays found in config file or automatically
root@badger-System-Product-Name:/home/badger#

```

what next?

---

### Post by darkod on 2015-10-28
I was also surprised it assembled automatically because there are no array definitions in mdadm.conf. Well, the good news is it assembles and looks good from mdadm point of view.
Now you have two options:
1. If you need to access the data urgently and do a backup copy for example, you can try mounting it, or
2. If you rather prefer to get it to full raid5 stage you can add the new disk and let it rebuild.

If you decide to add the new disk I would connect it to another machine if possible and zero the superblocks on both partitions. It was included in the failed rebuild so the superblocks might confuse it like it's belonging to the array. Zeroing the superblock info allows you to add the partitions as brand new.

---

### Post by Badger3x on 2015-10-28
> **darkod said:**
> I was also surprised it assembled automatically because there are no array definitions in mdadm.conf. Well, the good news is it assembles and looks good from mdadm point of view.
Now you have two options:
1. If you need to access the data urgently and do a backup copy for example, you can try mounting it, or
2. If you rather prefer to get it to full raid5 stage you can add the new disk and let it rebuild.

If you decide to add the new disk I would connect it to another machine if possible and zero the superblocks on both partitions. It was included in the failed rebuild so the superblocks might confuse it like it's belonging to the array. Zeroing the superblock info allows you to add the partitions as brand new.

I was going to go with option 1- backup what I can before anything else... 
which steps should I try to mount it safely?

---

### Post by darkod on 2015-10-28
Well, you have lvm right? So first would be to activate it with
```
sudo vgchange -ay
```

Hopefully that activates the lv correctly. After that I think it's best to try fsck to make sure filesystem is ok
```
sudo fsck /dev/vg/lv
```

Adjust the vg and lv name as necessary. If that reports ok, you can mount at any mount point you prefer
```
sudo mount /dev/vg/lv /mountpoint
```

That should be it. Hopefully the slot 4 disk that had errors is not very close to failure. Because the fsck and later copying the data will create load on the disks.
But trying a rebuild with the new disk also will create load, so you are in a situation where both options have some risk. Only thing you can do is keep your fingers crossed. All in all, I guess the copy should be less load than a full rebuild...

---

### Post by Badger3x on 2015-10-28
> **darkod said:**
> Well, you have lvm right? So first would be to activate it with
```
sudo vgchange -ay
```

Hopefully that activates the lv correctly. After that I think it's best to try fsck to make sure filesystem is ok
```
sudo fsck /dev/vg/lv
```

Adjust the vg and lv name as necessary. If that reports ok, you can mount at any mount point you prefer
```
sudo mount /dev/vg/lv /mountpoint
```



```
root@badger-System-Product-Name:/home/badger# sudo vgchange -ay
  2 logical volume(s) in volume group "vg0" now active
root@badger-System-Product-Name:/home/badger# fsck /dev/vg0/lv0
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
Superblock has an invalid journal (inode 8).
Clear<y>? no
fsck.ext3: Illegal inode number while checking ext3 journal for /dev/mapper/vg0-lv0

/dev/mapper/vg0-lv0: ********** WARNING: Filesystem still has errors **********

```

eeeek - too scared to say Y to clear question. So close now I can taste success, but don't want to hose it at the last second...




```

root@badger-System-Product-Name:/home/badger# mke2fs -n /dev/vg0/lv0
mke2fs 1.42.9 (4-Feb-2014)
/dev/vg0/lv0 alignment is offset by 65536 bytes.
This may result in very poor performance, (re)-partitioning suggested.
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=64 blocks, Stripe width=256 blocks
243892224 inodes, 1951137792 blocks
97556889 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
59544 block groups
32768 blocks per group, 32768 fragments per group
4096 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848, 512000000, 550731776, 644972544, 1934917632

```
So, what is safer, choosing clear or using a backup superblock?

---

### Post by darkod on 2015-10-29
I don't know if that fsck message is dangerous or not. I assume you will google the journal message too.

As for mke2fs, isn't that the same as mkfs which is used for creating filesystems (formatting)? I wouldn't play around with it too much. The alignment comment is worthless anyway because you have lvm. The alignment is for partitions on the physical disks.

---

### Post by darkod on 2015-10-29
Check out this tutorial:[https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

It gives some pointers and supposedly this operation is not as risky as it sounds.

In general you should be ok letting fsck fix it but I understand that you are worried about the data. I would be too. You might want to run fsck with -y option to avoid answering yes to each block it wants to fix.
Although the above tutorial uses fsck in a different way, basically just to restore a superblock backup.

---

### Post by Badger3x on 2015-10-29
> **darkod said:**
> Check out this tutorial:[https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

It gives some pointers and supposedly this operation is not as risky as it sounds.

In general you should be ok letting fsck fix it but I understand that you are worried about the data. I would be too. You might want to run fsck with -y option to avoid answering yes to each block it wants to fix.
Although the above tutorial uses fsck in a different way, basically just to restore a superblock backup.

Thanks darkod - i tried the superblock restore route which didnt seem to help, so am letting fsck have its way now.
it is presently fixing a million inode iblock thinks - seem slightly different sizes to what it thought they ought to have been.
Fingers and toes crossed. Wish me luck.

---

