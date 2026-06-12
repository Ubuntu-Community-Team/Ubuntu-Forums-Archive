---
title: "Converting existing RAID1 (where /root, /swap, /usr, and /var reside) to RAID10"
date: 2008-06-01
forum: Server Platforms
---

### Post by go out and enjoy the sun on 2008-06-01
Hiya! 

There are hundreds, thousands of articles and threads about software RAID, how to set it up and the possible problems (and solutions) and I admit to having trawled through a good many of them for information I could use in resolving my particular problem. I confess, however, that I'm not sophisticated enough to adapt the knowledge I've come across in the resolution of the issues I'm faced with, and it's for this reason I'm starting this thread, hoping what seems so opaque to me might be clear and simple to someone cleverer that I am.

My Hardy Heron system has 4 x 160 GB SATA harddrives, in which the HDDs are presently in (software) RAID1 in the following way:

```
cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda2[0] sdb2[1]
      156055296 blocks [2/2] [UU]
      
md0 : active raid1 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      192640 blocks [4/4] [UUUU]
      
unused devices: <none>
```

Note that md0 is a 4-way mirror of the devices /dev/sda1, /dev/sdb1, /dev/sdc1, and /dev/sdd1, while md1 is presently just a simple RAID1 mirror of devices /dev/sda2 and /dev/sdb2. The remaining devices /dev/sdc2 and /dev/sdd2 are presently not involved in the configuration. I left these out when I originally set my system up because I couldn't figure out how to get them into RAID10 (or RAID1+0, if you like) with the other two partitions /dev/sda2 and /dev/sdb2. It's my plan now to finally complete the set-up and create the RAID10 device md10 from the existing mirror md1 and a new one md2, the last which will be made up of /dev/sdc2 and /dev/sdd2. Please note that the system and root partitions are mounted and active already in RAID, so whatever changes I need to make that temporarily deactivates the RAID device that contains them will make the system unavailable.

Here is some more information.

The RAID device md0 contains just /boot :

```
sudo fdisk -l /dev/md0

Disk /dev/md0: 197 MB, 197263360 bytes
2 heads, 4 sectors/track, 48160 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```

... and md1 contains the rest of the filesystems, including root, swap, etc.:

```
sudo fdisk -l /dev/md1

Disk /dev/md1: 159.8 GB, 159800623104 bytes
2 heads, 4 sectors/track, 39013824 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table
```

The entire system on md1 is in LVM(2) in the following way:

```
sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/md1
  VG Name               vol_grp
  PV Size               148.83 GB / not usable 1.75 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              38099
  Free PE               0
  Allocated PE          38099
  PV UUID               8394Rm-AU72-6RZ7-5RQG-NWdR-R74D-wuREIu
```

```
sudo lvscan
  ACTIVE            '/dev/vol_grp/swap' [2.00 GB] inherit
  ACTIVE            '/dev/vol_grp/root' [3.50 GB] inherit
  ACTIVE            '/dev/vol_grp/home' [10.00 GB] inherit
  ACTIVE            '/dev/vol_grp/var-log' [2.00 GB] inherit
  ACTIVE            '/dev/vol_grp/tmp' [5.00 GB] inherit
  ACTIVE            '/dev/vol_grp/usr' [20.00 GB] inherit
  ACTIVE            '/dev/vol_grp/var' [20.00 GB] inherit
  ACTIVE            '/dev/vol_grp/usr-local' [5.00 GB] inherit
  ACTIVE            '/dev/vol_grp/store' [81.32 GB] inherit
```

... such that the current situation looks like this:

```
sudo df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/mapper/vol_grp-root
                      3.5G  331M  3.2G  10% /
varrun                2.0G  116K  2.0G   1% /var/run
varlock               2.0G  4.0K  2.0G   1% /var/lock
udev                  2.0G  124K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
lrm                   2.0G   43M  1.9G   3% /lib/modules/2.6.24-17-generic/volatile
/dev/mapper/vol_grp-home
                       10G   86M   10G   1% /home
/dev/mapper/vol_grp-tmp
                      5.0G   33M  5.0G   1% /tmp
/dev/mapper/vol_grp-usr
                       20G  1.3G   19G   7% /usr
/dev/mapper/vol_grp-usr--local
                      5.0G   33M  5.0G   1% /usr/local
/dev/mapper/vol_grp-var
                       20G  354M   20G   2% /var
/dev/mapper/vol_grp-var--log
                      2.0G   40M  2.0G   2% /var/log
/dev/mapper/vol_grp-store
                       82G  7.4G   74G  10% /store
```

```
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ccf7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+  fd  Linux raid autodetect
/dev/sda2              25       19452   156055410   fd  Linux raid autodetect

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d1b00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          24      192748+  fd  Linux raid autodetect
/dev/sdb2              25       19457   156095572+  fd  Linux raid autodetect

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002dc62

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          24      192748+  fd  Linux raid autodetect
/dev/sdc2              25       19457   156095572+  fd  Linux raid autodetect

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c9c2d38

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1          24      192748+  fd  Linux raid autodetect
/dev/sdd2              25       19457   156095572+  fd  Linux raid autodetect

Disk /dev/md0: 197 MB, 197263360 bytes
2 heads, 4 sectors/track, 48160 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 159.8 GB, 159800623104 bytes
2 heads, 4 sectors/track, 39013824 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table
```

I'm using ReiserFS across the board on all mounts, from /boot to /store.

Whew!

Just to re-iterate, what I'd like to do is to involve the remaining unused drives /dev/sdc2 and /dev/sdd2, RAID them up in a RAID1 device (/dev/md2), and then stripe /dev/md1 and /dev/md2 together to achieve RAID10 that is constituted of the currently existing (and presently active, in particular with respect to root and system) RAID1 device, and the new RAID1 system.

Thanks in advance; I appreciate your advice.

---

