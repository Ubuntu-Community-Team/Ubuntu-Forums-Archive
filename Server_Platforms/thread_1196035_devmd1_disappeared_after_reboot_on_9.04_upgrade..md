---
title: "/dev/md1 disappeared after reboot on 9.04 upgrade."
date: 2009-06-24
forum: Server Platforms
---

### Post by coolaj86 on 2009-06-24
Last night I finally upgraded to 9.04. When I rebooted this morning /dev/md1 had disappeared and I had to use CTRL-D to boot the system.

If you are knowledgeable and kind enough to look over this information, I'll get a girlfriend and kindly ask her to bake you cookies.

Here's the basic layout:
SWAP PRI=1 - the first partition of each drive is added here
RAID 1 - Mirrored - /dev/md0 mounts as /
RAID 0 - Striped - /dev/md1 mounts as /mnt/data
No RAID - Normal - /dev/sdc2 mounts as /mnt/backup

Here are some things I think are useful, but don't know what do do with:
```

ls /dev/md*
/dev/md0  /dev/md_d1  /dev/md_d1p1  /dev/md_d1p2  /dev/md_d1p3	/dev/md_d1p4

/dev/md:
d1  d1p1  d1p2	d1p3  d1p4

mdadm --query /dev/sda5
/dev/sda5: is not an md array
/dev/sda5: device 0 in 3 device undetected raid0 /dev/.tmp.md1.  Use mdadm --examine for more detail.

mdadm --examine /dev/sda5
/dev/sda5:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1f78be10:e0fa3727:dbefc0ff:bf34ee59 (local to host ubu-dragon)
  Creation Time : Sun Feb 15 22:09:25 2009
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1

    Update Time : Sun Feb 15 22:09:25 2009
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d7f5de82 - correct
         Events : 1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        5        0      active sync   /dev/sda5

   0     0       8        5        0      active sync   /dev/sda5
   1     1       8       21        1      active sync   /dev/sdb5
   2     2       8       37        2      active sync

fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05358c5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1052226   82  Linux swap / Solaris
/dev/sda2             132         784     5245222+  fd  Linux raid autodetect
/dev/sda3   *         785         810      208845   83  Linux
/dev/sda4             811        9729    71641867+   5  Extended
/dev/sda5             811        7290    52050568+  fd  Linux raid autodetect
/dev/sda6            7291        9729    19591236   fd  Linux raid autodetect

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x182f182e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         131     1052226   82  Linux swap / Solaris
/dev/sdb2             132         784     5245222+  fd  Linux raid autodetect
/dev/sdb3   *         785         810      208845   83  Linux
/dev/sdb4             811        7296    52098795    5  Extended
/dev/sdb5             811        7296    52098763+  fd  Linux raid autodetect

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         124      995998+  82  Linux swap / Solaris
/dev/sdc2   *         125       19929   159083662+  83  Linux

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009ca63

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         131     1052226   82  Linux swap / Solaris
/dev/sdd2             132         784     5245222+  fd  Linux raid autodetect
/dev/sdd3             785         810      208845   83  Linux
/dev/sdd4             811        9729    71641867+   5  Extended
/dev/sdd5             811        7296    52098763+  fd  Linux raid autodetect
/dev/sdd6            7297        9729    19543041   fd  Linux raid autodetect

Disk /dev/md0: 16.1 GB, 16113008640 bytes
2 heads, 4 sectors/track, 3933840 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```


As it happens I think the last thing I did before I left my computer for the night was a backup. So in the worst case I should be able to copy the 140gb back over, but I'd prefer to fix the problem and prevent it from happening again.

---

### Post by coolaj86 on 2009-06-25
I posed this question differently in another thread and got just the hint I needed:

[http://ubuntuforums.org/showthread.php?p=7513113#post7513113](http://ubuntuforums.org/showthread.php?p=7513113#post7513113)

---

### Post by moodog on 2009-11-24
I'm having the same problem - I've just upgraded from 8.10 to 9.04. For some reason as part of the upgrade my disks were relabelled - what was initially /dev/sdb is now /dev/sde. As a result of this (or something else), /dev/md0 no longer works as expected. I've run some of the above commands, and specifically when I run mdadm I get the following:

```
#mdadm --assemble /dev/md0 /dev/sda /dev/sdb /dev/sdc
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has no superblock - assembly aborted
```

The funny thing is that I've run this command after a number of reboots, and on each occasion the device that is busy has changed - i.e. it was initially sdc, then sdb, now sda etc.

I have three 1TB disks that are fully partitioned to be in the array - /dev/sda /dev/sdb /dev/sdc.

Any help would be greatly appreciated. Below is the output of some other commands that may be useful.



```
# ls /dev/md*

/dev/md0  /dev/md_d0  /dev/md_d0p1  /dev/md_d0p2  /dev/md_d0p3  /dev/md_d0p4

/dev/md:
d0  d0p1  d0p2  d0p3  d0p4


# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b285d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2932    23551258+  83  Linux
/dev/sdd2            5646       19457   110944890   83  Linux
/dev/sdd3            2933        3095     1309297+  82  Linux swap / Solaris
/dev/sdd4            3096        5645    20482875    5  Extended
/dev/sdd5            3096        5007    15358108+  83  Linux
/dev/sdd6            5008        5645     5124703+  83  Linux

Partition table entries are not in disk order

Disk /dev/sde: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e2ab4

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       36483   293049666   83  Linux

Disk /dev/md_d0: 2000.4 GB, 2000409591808 bytes
2 heads, 4 sectors/track, 488381248 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md_d0 doesn't contain a valid partition table

```

---

### Post by moodog on 2009-11-24
Additional info - there are a few weird things here - first, why did the disks get renamed, but moving on.
the file system on the device is xfs - for some reason in the upgrade, xfs wasn't installed, so I manually installed it.

running lsof gives the following

```
lsof | grep sda 
xfsdatad/ 2242                root  cwd       DIR       8,49     4096          2 /
xfsdatad/ 2242                root  rtd       DIR       8,49     4096          2 /
xfsdatad/ 2242                root  txt   unknown                                /proc/2242/exe
xfsdatad/ 2243                root  cwd       DIR       8,49     4096          2 /
xfsdatad/ 2243                root  rtd       DIR       8,49     4096          2 /
xfsdatad/ 2243                root  txt   unknown                                /proc/2243/exe
```

so it appears that xfs has the disk locked for some reason - I'm unsure why, as it shouldn't be able to access the disk, as the file system is on the raid array...

---

### Post by moodog on 2009-11-24
ooooook, not sure what's going on here, but something changed, and when I ran cat /proc/mdstat it contained this:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : active raid5 sdb[1] sdc[2] sda[0]
      1953524992 blocks level 5, 32k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>

```

so I changed fstab from md0 to md_d0, and mount-a worked. Not sure why this happened, or if it's going to happen again. Any ideas?

---

