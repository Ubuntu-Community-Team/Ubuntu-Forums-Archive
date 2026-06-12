---
title: "RAID 5 won't mount"
date: 2015-11-27
forum: Server Platforms
---

### Post by jordelver on 2015-11-27
Hi,
I have a RAID 5 that will not mount. I think one or more of the disks is dead.

I've tried forcing it to start but it says that there are not enough disks to start.

I have a feeling that the UUIDs have changed or something but I set this up many years ago and have since forgotten all mdadm knowledge ;)

Can someone point me in the right direction?

**cat /proc/mdstat**

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[3](S) sdb1[1](S) sdc1[2](S) sdf1[4](S)
      6348919744 blocks
       
unused devices: <none>

```

Output from **fdisk -l**
```

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      182401  1465136001   fd  Linux RAID autodetect

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001   fd  Linux RAID autodetect

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      182401  1465136001   fd  Linux RAID autodetect

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c668f

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        9360    75182080   83  Linux
/dev/sde2            9360        9730     2966529    5  Extended
/dev/sde5            9360        9730     2966528   82  Linux swap / Solaris

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001   fd  Linux RAID autodetect

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf7d64173

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      243201  1953512001   fd  Linux RAID autodetect
Partition 1 does not start on physical sector boundary.

Disk /dev/sdg: 4110 MB, 4110230016 bytes
255 heads, 63 sectors/track, 499 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1         500     4013895+   b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1023, 254, 63) logical=(0, 0, 3)
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(499, 180, 18)

```

Output of **mdadm --examine /dev/sd[a-z]1 | egrep 'Event|/dev/sd'**

```

/dev/sdb1:
         Events : 3080720
this     1       8       17        1      active sync   /dev/sdb1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       81        3      active sync   /dev/sdf1
   4     4       8       49        4      active sync   /dev/sdd1
/dev/sdc1:
         Events : 3080720
this     2       8       65        2      active sync   /dev/sde1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       81        3      active sync   /dev/sdf1
   4     4       8       49        4      active sync   /dev/sdd1
/dev/sdd1:
         Events : 3080720
this     3       8       81        3      active sync   /dev/sdf1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       81        3      active sync   /dev/sdf1
   4     4       8       49        4      active sync   /dev/sdd1
/dev/sdf1:
         Events : 3080720
this     4       8       49        4      active sync   /dev/sdd1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       81        3      active sync   /dev/sdf1
   4     4       8       49        4      active sync   /dev/sdd1

```

Output from **blkid**

```

/dev/sdb1: UUID="f51f02cd-3b5c-9fa9-a40e-4b4e93ecf45d" TYPE="linux_raid_member" 
/dev/sdd1: UUID="f51f02cd-3b5c-9fa9-a40e-4b4e93ecf45d" TYPE="linux_raid_member" 
/dev/sde1: UUID="85824bcf-e53a-4e6f-84c7-480541438d04" TYPE="ext4" 
/dev/sde5: UUID="a44be20f-c7dc-44ae-9e8c-a08666009a65" TYPE="swap" 
/dev/sdc1: UUID="f51f02cd-3b5c-9fa9-a40e-4b4e93ecf45d" TYPE="linux_raid_member" 
/dev/sdf1: UUID="f51f02cd-3b5c-9fa9-a40e-4b4e93ecf45d" TYPE="linux_raid_member" 
/dev/sdg1: LABEL="UNTITLED" UUID="49FB-17DD" TYPE="vfat"

```

Contents of **mdadm.conf**

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
MAILADDR root

# definitions of existing MD arrays
#ARRAY /dev/md0 level=raid5 num-devices=4 metadata=0.90 UUID=f51f02cd:3b5c9fa9:a40e4b4e:93ecf45d
ARRAY /dev/md0 level=raid5 num-devices=5 metadata=0.90 UUID=f51f02cd:3b5c9fa9:a40e4b4e:93ecf45d

# This file was auto-generated on Tue, 13 Jul 2010 17:16:04 +0100
# by mkconf $Id$

```

---

### Post by darkod on 2015-11-27
How many devices you have in the raid5, is it 5 or 4? The --examine shows four, but mdadm.conf shows five (the ARRAY definition with four members is commented out).

Also the --examine shows sde1 as raid member which is obviously wrong. It should be sdc1 and maybe sda1 too if you have five members.

be careful what commands you run because you can mess it up further. So far so good, nothing dangerous was executed.

PS. How come sda1 shows up in fdisk and with Linux Raid Autodetect type, but it does not show in blkid? Could the sda disk be faulty?

If that were to be true and the total number of members is five, and if the system is currently "confused" trying to use sde1 instead of sdc1, that could be a reason why it can't start. Because it would be trying to start a five member raid5 array without two members (sda1 and sdc1). Raid5 would not start with two members missing. But all of this is speculation. It could give you some ideas where to look...

PPS. What you could try is assembling /dev/md0 with only four members (sdb1, sdc1, sdd1 and sdf1). According to --examine the Events counters are identical on these four partitions, which is very good. Regardless whether the array has four or five members it should start with these four members present. If you need help with the command, ask...

---

### Post by jordelver on 2015-11-27
> **darkod said:**
> How many devices you have in the raid5, is it 5 or 4? The --examine shows four, but mdadm.conf shows five (the ARRAY definition with four members is commented out).

Yes, that is confusing, sorry. I took a look at fixing this a few months ago and I think that was my attempt at fixing it then.

There are 5 disks in the array.

There are 6 disks in total, that's used for the OS. I think that should be /dev/sde

> **darkod said:**
> 
Also the --examine shows sde1 as raid member which is obviously wrong. It should be sdc1 and maybe sda1 too if you have five members.


Yeah, as above. You are right. I'm wonder whether sda1 died and then the disks got messed up some how?

> **darkod said:**
> 
PS. How come sda1 shows up in fdisk and with Linux Raid Autodetect type, but it does not show in blkid? Could the sda disk be faulty?


This sounds correct.

> **darkod said:**
> 
If that were to be true and the total number of members is five, and if the system is currently "confused" trying to use sde1 instead of sdc1, that could be a reason why it can't start. Because it would be trying to start a five member raid5 array without two members (sda1 and sdc1). Raid5 would not start with two members missing. But all of this is speculation. It could give you some ideas where to look...

PPS. What you could try is assembling /dev/md0 with only four members (sdb1, sdc1, sdd1 and sdf1). According to --examine the Events counters are identical on these four partitions, which is very good. Regardless whether the array has four or five members it should start with these four members present. If you need help with the command, ask...

Yes, please :) I think that this is recoverable. I think only one disk has died and the others are now confused...

---

### Post by darkod on 2015-11-27
Hmmm, first lets try something like:
```
sudo mdadm --assemble --verbose /dev/md0 /dev/sd[bcdf]1
```

Post how that goes...

---

### Post by jordelver on 2015-11-27
> **darkod said:**
> Hmmm, first lets try something like:
```
sudo mdadm --assemble --verbose /dev/md0 /dev/sd[bcdf]1
```

Post how that goes...

Oh, dear. Things have taken a turn for the worse.

I started it up and now it doesn't boot, just hangs at an (iniramfs) prompt :(

It says EXT4-fs (sda1): error loading journal. I think it's related to the UUIDs because it seems like it can't find the boot disk now.

I unplugged all the drives except the OS to see if it would boot without them connected and it doesn't.

---

### Post by darkod on 2015-11-27
I am confused, I thought the server is already running (even with the raid down). It does not boot after you ran that command or before you had a chance to run it? If you did run it, what did the output show? That's why I used the --verbose option too.

Could the OS disk actually be playing up on you? It should boot, especially with the raid disks disconnected. But be careful when disconnecting, it's better to put back the disks in the same order.

So what's current status? Doesn't boot at all with only the OS disk? Any error messages? What is happening exactly?

---

### Post by darkod on 2015-11-27
You can also leave the disks attached as they were and boot the machine with the desktop cd/usb into live mode. That will allow you to "look inside" and figure out what is going on. Especially to look into the raid because that's where all the important data is I suppose.

One example is that mdadm can be configured to boot degraded or not, depending what you selected when installing. If you selected No and the array is degraded (4 members out of 5), it will not boot even when the OS disk is good because that was the selection made for mdadm. That is just one example...

---

### Post by jordelver on 2015-12-01
Thanks. I booted from a USB stick and have now removed the bad RAID drive. It still doesn't boot because the OS drive seems to also have died. I plan on adding the RAID members to new hardware when I get it. Thanks for your help.

---

