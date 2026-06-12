---
title: "RAID status definition"
date: 2011-09-03
forum: Server Platforms
---

### Post by brighty22 on 2011-09-03
Hi,
Just checked the status of RAID arrays on my server; was presented with these:

```
george@bright2a:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid5 sdc2[2] sdd2[3] sda2[0] sdb2[1]
      877056 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]

md0 : active raid1 sdd1[3] sdc1[2] sda1[0] sdb1[1]
      96244 blocks super 1.2 [4/4] [UUUU]

md2 : active raid5 sdb3[1] sdc3[2] sdd3[3] sda3[0]
      4394236416 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      [=======>.............]  check = 39.7% (582118284/1464745472) finish=157.7min speed=93256K/sec

unused devices: <none>
```

```
george@bright2a:~$ sudo mdadm --detail /dev/md2
[sudo] password for george:
/dev/md2:
        Version : 1.2
  Creation Time : Wed Jul  6 22:36:53 2011
     Raid Level : raid5
     Array Size : 4394236416 (4190.67 GiB 4499.70 GB)
  Used Dev Size : 1464745472 (1396.89 GiB 1499.90 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Sun Sep  4 03:27:58 2011
          State : clean, recovering
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

 Rebuild Status : 40% complete

           Name : bright2a:2  (local to host bright2a)
           UUID : b1c8c0be:56670ac0:536b2570:ba1fc479
         Events : 184

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3
       2       8       35        2      active sync   /dev/sdc3
       3       8       51        3      active sync   /dev/sdd3
```

I've never seen this before and am slightly worried why 'md2' is being checked - is it something scheduled automatically, or an indication of disk errors? I've tried Google, but haven't been able to find any solid definitions of RAID statuses. Can anyone help?

Thanks

---

### Post by ian dobson on 2011-09-04
Hi,

First sunday of the month, all raid arrays are checked.

Have a look at /etc/cron.d/mdadm and  /usr/share/mdadm/checkarray

So it's normal, if you don't want it just edit the cron job.


Regards
Ian Dobson

---

### Post by rubylaser on 2011-09-04
The easiest way to tell if it's just mdadm's scheduled check or if you've had a problem is to check these two values.

```
cat /sys/block/md0/md/degraded
cat /sys/block/md0/md/sync_action
```

And dmesg for messages about your array

```
dmesg | grep md2
```

---

### Post by brighty22 on 2011-09-04
Thanks to you both.

@rubylaser
Output of the first two looks fine (0 and idle respectively), but the third gave this:

```
george@bright2a:~$ dmesg | grep md2
[    1.783845] md/raid:md2: device sdc3 operational as raid disk 2
[    1.783847] md/raid:md2: device sdd3 operational as raid disk 3
[    1.783849] md/raid:md2: device sdb3 operational as raid disk 1
[    1.783851] md/raid:md2: device sda3 operational as raid disk 0
[    1.784248] md/raid:md2: allocated 4222kB
[    1.784285] md/raid:md2: raid level 5 active with 4 out of 4 devices, algorithm 2
[    1.784326] md2: detected capacity change from 0 to 4499698089984
[    1.792608]  md2: unknown partition table
[    1.973457] EXT4-fs (md2): INFO: recovery required on readonly filesystem
[    1.973461] EXT4-fs (md2): write access will be enabled during recovery
[    3.389214] EXT4-fs (md2): orphan cleanup on readonly fs
[    3.389235] EXT4-fs (md2): ext4_orphan_cleanup: deleting unreferenced inode 228065293
[    3.389273] EXT4-fs (md2): ext4_orphan_cleanup: deleting unreferenced inode 228065292
[    3.389280] EXT4-fs (md2): ext4_orphan_cleanup: deleting unreferenced inode 228065291
[    3.389287] EXT4-fs (md2): ext4_orphan_cleanup: deleting unreferenced inode 228065290
[    3.389293] EXT4-fs (md2): ext4_orphan_cleanup: deleting unreferenced inode 228065289
[    3.389298] EXT4-fs (md2): 5 orphan inodes deleted
[    3.389300] EXT4-fs (md2): recovery complete
[    3.492845] EXT4-fs (md2): mounted filesystem with ordered data mode. Opts: (null)
[    6.409530] EXT4-fs (md2): re-mounted. Opts: errors=remount-ro

```

Not sure what an unreferenced/orphaned inode is...

---

### Post by ian dobson on 2011-09-04
> **brighty22 said:**
> Thanks to you both.

@rubylaser
Output of the first two looks fine (0 and idle respectively), but the third gave this:

```
george@bright2a:~$ dmesg | grep md2
[    1.783845] md/raid:md2: device sdc3 operational as raid disk 2
[    1.783847] md/raid:md2: device sdd3 operational as raid disk 3
[    1.783849] md/raid:md2: device sdb3 operational as raid disk 1
[    1.783851] md/raid:md2: device sda3 operational as raid disk 0
[    1.784248] md/raid:md2: allocated 4222kB
[    1.784285] md/raid:md2: raid level 5 active with 4 out of 4 devices, algorithm 2
[    1.784326] md2: detected capacity change from 0 to 4499698089984
[    1.792608]  md2: unknown partition table
[    1.973457] EXT4-fs (md2): INFO: recovery required on readonly filesystem
[    1.973461] EXT4-fs (md2): write access will be enabled during recovery
[    3.389214] EXT4-fs (md2): orphan cleanup on readonly fs
[    3.389235] EXT4-fs (md2): ext4_orphan_cleanup: deleting unreferenced inode 228065293
[    3.389273] EXT4-fs (md2): ext4_orphan_cleanup: deleting unreferenced inode 228065292
[    3.389280] EXT4-fs (md2): ext4_orphan_cleanup: deleting unreferenced inode 228065291
[    3.389287] EXT4-fs (md2): ext4_orphan_cleanup: deleting unreferenced inode 228065290
[    3.389293] EXT4-fs (md2): ext4_orphan_cleanup: deleting unreferenced inode 228065289
[    3.389298] EXT4-fs (md2): 5 orphan inodes deleted
[    3.389300] EXT4-fs (md2): recovery complete
[    3.492845] EXT4-fs (md2): mounted filesystem with ordered data mode. Opts: (null)
[    6.409530] EXT4-fs (md2): re-mounted. Opts: errors=remount-ro

```

Not sure what an unreferenced/orphaned inode is...

When you boot, the ext4 driver checks the filesystem/goes through the journel cleaning up if the file system wasn't shutdown correctly.

Do you have any other messages in dmesg for md2. So it looks as if your box didn't shutdown correctly and on the next boot the system checked the fs and ran a raid array scan.

Regards
Ian Dobson

---

### Post by brighty22 on 2011-09-04
Fair enough. I believe it was shut down correctly (shutdown -h now).. ah well. Might be the first Sunday of the month check. Thanks for explaining :)

---

