---
title: "Mdadm says superblock is persistent, fsck disagrees"
date: 2014-03-31
forum: Server Platforms
---

### Post by ooboontwo on 2014-03-31
**PLEASE SEE UPDATE IN SECOND POST**

Hey guys,

I am having problems with a simple raid(1) setup.

I have created an array (/dev/md127) out of /dev/sda1 and /dev/sdc1. Here's what I get when I execute: mdadm --detail /dev/md127

```
/dev/md127:
        Version : 1.2
  Creation Time : Wed Mar 26 15:40:26 2014
     Raid Level : raid1
     Array Size : 976629568 (931.39 GiB 1000.07 GB)
  Used Dev Size : 976629568 (931.39 GiB 1000.07 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Mar 31 15:39:22 2014
          State : active, resyncing
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

  Resync Status : 56% complete

           Name : sabsrv:0  (local to host sabsrv)
           UUID : 44818573:07978ec7:66a9a594:6dbba23b
         Events : 23

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       33        1      active sync   /dev/sdc1
```

Notice that it tells me the superblock is persistent.

The issue is... I can't mount it. I know it is syncing right now, but that shouldn't stop me from being able to mount the array. So here's what I get when I try:

```
root@sabsrv:~# mount -t ext4 /dev/md127 /mnt/live/working
mount: wrong fs type, bad option, bad superblock on /dev/md127,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Hmm... that's strange because the fs is definitely ext4. I even double-checked using parted. Yep, /dev/sda1 and /dev/sdc1 are both listed as ext4 but wait... what's this?

```
Error: /dev/md127: unrecognised disk label
```

Ah, the plot thickens. So, now I try fsck on /dev/md127 and here's what I get:

```

root@sabsrv:~# fsck.ext4 /dev/md127
e2fsck 1.42 (29-Nov-2011)
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/md127

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

[sarcasm]Greaaat[/sarcasm]

Here's the good news: There is no data on the disks, so I have no problem wiping them clean and starting over but I don't know where to begin. What steps should I take to troubleshoot the disks as they currently are? Or, should I just destroy the array, reformat the disks and try, try again?

Thanks for your help guys and I hope this is in the right forum. I am using Ubuntu Server 12.04.3 (Mods, please move elsewhere if required.)

Blessings,
Cody

---

### Post by ooboontwo on 2014-04-01
So, just a little update:

I went ahead and removed the array using mdadm --stop, mdadm --zero-superblock /dev/sda1 (and sdc1), and mdadm --remove.

Next, I wiped the filesystems on /dev/sda1 and dev/sdc1.

I ran: mkfs -t ext3 /dev/sda1
and
mkfs -t ext3 /dev/sdc1

(I decided to go with ext3 just for the heck of it, rather than ext4.)

I was then able to successfully mount /dev/sda1 and /dev/sdc1. I also ran fsck.ext3 on both and received no errors.

Finally, I recreated the array using:

```
mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdc1
```

It seemed to be created successfully and mdstat now shows:

```
root@sabsrv:/mnt# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdc1[1] sda1[0]
      976629568 blocks super 1.2 [2/2] [UU]
      [==>..................]  resync = 10.2% (99648704/976629568) finish=131.8min speed=110841K/sec
```

The problem?

I still can't mount this thing. Here's some more info...

/etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=94800779-3276-4159-8fdd-1f35db344bca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8a777bdf-08fd-4fb0-9244-4f5675730a5e none            swap    sw              0       0
/dev/md0        /mnt/live/working       ext3    defaults        0       2
/dev/sdd        /mnt/archive    ext3    defaults        0       3
```

/etc/mdadm/mdadm.conf:

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

# This file was auto-generated on Fri, 21 Mar 2014 15:16:37 -0500
# by mkconf $Id$
ARRAY /dev/md/0 metadata=1.2 UUID=044f65c9:ac4db1ee:3c04ac2c:ac539d70 name=sabsrv:0
```

mdadm --detail /dev/md0:

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

# This file was auto-generated on Fri, 21 Mar 2014 15:16:37 -0500
# by mkconf $Id$
ARRAY /dev/md/0 metadata=1.2 UUID=044f65c9:ac4db1ee:3c04ac2c:ac539d70 name=sabsrv:0
root@sabsrv:/mnt# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Tue Apr  1 14:20:31 2014
     Raid Level : raid1
     Array Size : 976629568 (931.39 GiB 1000.07 GB)
  Used Dev Size : 976629568 (931.39 GiB 1000.07 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Tue Apr  1 14:40:32 2014
          State : active, resyncing
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

  Resync Status : 16% complete

           Name : sabsrv:0  (local to host sabsrv)
           UUID : 044f65c9:ac4db1ee:3c04ac2c:ac539d70
         Events : 5

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       33        1      active sync   /dev/sdc1


```

fsck.ext3 /dev/md0:

```
e2fsck 1.42 (29-Nov-2011)
fsck.ext3: Superblock invalid, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

---

### Post by steeldriver on 2014-04-01
I'm not a RAID expert, but normally you would create the array out of bare unformatted partitions (or possibly whole disks) and **then **create the desired fs (ext2/3/4 or whatever) **on top** of the /dev/mdXX device - in other words, think of the array as a virtual disk.

You seem to be trying to do it the other way around (trying to create an array from *formatted *disks, and expecting the original ext fs to be visible in the resulting array). I may be misunderstanding, but I don't think it can work like that.

---

### Post by ooboontwo on 2014-04-01
> **steeldriver said:**
> I'm not a RAID expert, but normally you would create the array out of bare unformatted partitions (or possibly whole disks) and **then **create the desired fs (ext2/3/4 or whatever) **on top** of the /dev/mdXX device - in other words, think of the array as a virtual disk.

You seem to be trying to do it the other way around (trying to create an array from *formatted *disks, and expecting the original ext fs to be visible in the resulting array). I may be misunderstanding, but I don't think it can work like that.
[B]
I feel like a complete idiot.[/B] You're absolutely right. I just created an ext3 filesystem on /dev/md0 and everything is working perfectly. Thank you!

---

