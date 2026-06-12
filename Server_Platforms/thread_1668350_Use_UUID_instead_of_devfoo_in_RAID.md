---
title: "Use UUID instead of /dev/foo in RAID?"
date: 2011-01-16
forum: Server Platforms
---

### Post by RobbanC on 2011-01-16
Hi!
I just installed a new file server with Ubuntu Server 10.10. Works great so far. I just wonder about a thing regarding my disks. Maybe someone can help me out?

My mobo has four SATA connectors and one IDE. At the moment I use the IDE for a flash-disk that holds the system and two SATA for a RAID1-storage. My disks are currently detected and used as follows:

/dev/sda   <- My flash-disk with the OS
/dev/sdb   <- Raid-member
/dev/sdc   <- Raid-member

The two latter above forms a raid-disk on /dev/md0 that I mount on /raid. 

But no problems so far...

If I plug in one or two more SATA-disks to use in my raid-config, my /dev/devices above change, since the new disks tend to come in "before" the disks I now use. If I plug in a new disk, all change to:

/dev/sda  <- New disk
/dev/sdb  <- My old /dev/sda (System-disk)
/dev/sdc  <- My old /dev/sdb
/dev/sdd  <- My old /dev/sdc

Ubuntu itself handles this pretty fine. I have entered the UUID.s in fstab so even if the /dev/[whatever] changes, the system will work. fstab looks like this:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda1 during installation
UUID=4a9d63a5-72d6-40c9-bc60-a61ce7e822a5 / ext4 errors=remount-ro 0 1

# swap was on /dev/sda5 during installation
UUID=c96a5e43-f583-42d9-8fba-df30a2505e26 none swap sw 0 0

# /tmp should be in RAM
tmpfs /tmp tmpfs mode=1777,size=512m

# Mount RAID-disks
/dev/md0  /raid  ext4  user,nosuid,nodev  0  0

```

[B]Now!
What I am worried about[/B] is my RAID-setup. If suddenly all disk-devices change their notation, how will that work?

I have searched if it is possible to somehow enter the UUID.s to use as RAID-devices, but I have not found anything useful.

That is: Somehow I want to use the UUID stated as "linux-raid-member" by blkid, instead of /dev/sdb and /dev/sdc in my RAID-config.

some outputs:
```

robban@cubert:/$ cat mdadm.conf
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
MAILADDR foo@banana.bar

# definitions of existing MD arrays

# This file was auto-generated on Mon, 10 Jan 2011 21:10:19 +0100
# by mkconf $Id$
DEVICE /dev/sdb
DEVICE /dev/sdb /dev/sdc
ARRAY /dev/md0 level=raid1 devices=/dev/sdb,/dev/sdc

```

```

robban@cubert:/$ sudo blkid
[sudo] password for robban:
/dev/sda1: UUID="4a9d63a5-72d6-40c9-bc60-a61ce7e822a5" TYPE="ext4"
/dev/sda5: UUID="c96a5e43-f583-42d9-8fba-df30a2505e26" TYPE="swap"
/dev/sdb: UUID="4fa25fa6-a342-d3cf-38fe-c9b2747d972e" TYPE="linux_raid_member"
/dev/md0: UUID="7c5d0d27-93f8-4036-9740-ca272415e410" TYPE="ext4"
/dev/sdc: UUID="4fa25fa6-a342-d3cf-38fe-c9b2747d972e" TYPE="linux_raid_member"

```

Any tips?

---

### Post by disabledaccount on 2011-01-16
You shouldn't worry about this, because by default md scans every disk/partition to find array superblocks (DEVICE partitions). This behaviour can be overridden by proper setting of DEVICE and ARRAY parameters in /etc/mdadm/mdadm.conf - but it makes sense only if you have many hdd's and/or many partitions. For DEVICE you can use UUID's instead of /dev/sdx

---

### Post by RobbanC on 2011-01-16
Thanks tomazzi!

So you are saying that, even if my mdadm.conf (as seen above) says that the raid uses sdb and sdc, it doesn't matter, since md scans for array superblocks?

Please confirm. I still don't have that warm and cozy feeling that my raid will work as supposed to when a disk fails, is removed or is added. :|

---

### Post by disabledaccount on 2011-01-17
> **RobbanC said:**
> So you are saying that, even if my mdadm.conf (as seen above) says that the raid uses sdb and sdc, it doesn't matter, since md scans for array superblocks?exactly :)
I have 4 arrays in my desktop that are working with default mdadm.conf.

---

### Post by RobbanC on 2011-01-17
Ok. Thanks again.

I tried failing some drives in a similar setup I have as a virtual mashine. Seem to work fine, as long as disks are marked as failed and removed properly. :)

If I change the whole setup, like adding, removing or moving disks, I need to change mdadm.conf according to in wich order my drives are detected.

I'm quite pleased with that. I just want to know how to deal with an eventual disk failure or what happens if I insert more disks. 
I don't want to loose my data if it's not "necessary", so to say. ;)

---

