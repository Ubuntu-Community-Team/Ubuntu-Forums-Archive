---
title: "Help properly deleting RAID array"
date: 2013-04-25
forum: Server Platforms
---

### Post by reedk on 2013-04-25
I have a hard drive with multiple partitions, two of which are active RAID1 arrays, and a third that contains a raid array I no longer want. I want to destroy that one raid array without damaging the others.

```
# fdisk /dev/sdc

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000c4ca4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    48828415    24413184   fd  Linux raid autodetect
/dev/sdc2        48830462  3907028991  1929099265    5  Extended
/dev/sdc5        48830464    56641535     3905536   82  Linux swap / Solaris
/dev/sdc6        56643584  1955078143   949217280   fd  Linux raid autodetect
     /dev/sdc7      1955080192  3853514751   949217280   fd  Linux raid autodetect
     /dev/sdc8      3853516800  3907028991    26756096   83  Linux

```

```
# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : active (auto-read-only) raid1 sdc1[1]
      24396672 blocks super 1.2 [2/1] [_U]
      
md1 : active raid1 sdc6[1] sda3[2]
      948309824 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sda1[0] sdb1[1]
      24396672 blocks super 1.2 [2/2] [UU]
      
md2 : active raid1 sdc7[1] sdb3[2]
      948309824 blocks super 1.2 [2/2] [UU]

```      


I want to banish the RAID /dev/127 from /dev/sdc1, without impacting the active RAIDs on the other partitions on that drive.

Is this as simple as mdadm --zero-superblock /dev/sdc1? Any thoughts anyone?

---

### Post by darkod on 2013-04-25
Also look in /etc/mdadm/mdadm.conf whether there ia an ARRAY definition for it. If there is, comment it out or delete it.

Then unmount it if it's mounted, and stop it:
sudo mdadm --stop /dev/md127

The zero the superblock for that partition.

That should be it.

---

### Post by reedk on 2013-04-25
That did it. I was afraid to zero that partition without some recommendation out of sheer fear. Thanks!

---

