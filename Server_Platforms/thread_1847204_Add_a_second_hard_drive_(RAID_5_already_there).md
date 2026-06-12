---
title: "Add a second hard drive (RAID 5 already there)"
date: 2011-09-20
forum: Server Platforms
---

### Post by DRouleau on 2011-09-20
Ubuntu 11.04 Server
What I'm trying to do is use the RAID 5 drives that are on my server.  My main partition is a mirror and that is working fine.  Just can't figure out how to "use" the RAID 5 Drives.  This is the info from fdisk -l:

Disk /dev/sda: 36.7 GB, 36698849280 bytes
255 heads, 63 sectors/track, 4461 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000efe56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        4462    35587073    5  Extended
/dev/sda5              32        4462    35587072   8e  Linux LVM

Disk /dev/sdb: 36.4 GB, 36397645824 bytes
255 heads, 63 sectors/track, 4425 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/dm-0: 34.3 GB, 34250686464 bytes
255 heads, 63 sectors/track, 4164 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 2143 MB, 2143289344 bytes
255 heads, 63 sectors/track, 260 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table


let me know if you need any more info.
Thanks in advance!

---

### Post by DRouleau on 2011-09-20
I think I have it, just need to "test" it...

---

### Post by DRouleau on 2011-09-20
Nope, no luck... gotta love false hope.

---

### Post by rubylaser on 2011-09-20
What's the output of these?
```
cat /proc/mdstat
```
```
mdadm --detail --scan
```
```
cat /etc/mdadm/mdadm.conf
```

---

### Post by DRouleau on 2011-09-20
Here is what you requested:

root@LinuxServer:~# cat /proc/mdstat
Personalities :
unused devices: <none>


root@LinuxServer:~# mdadm --detail --scan
root@LinuxServer:~#



root@LinuxServer:~# cat /etc/mdadm/mdadm.conf
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

# This file was auto-generated on Tue, 20 Sep 2011 13:21:30 -0400
# by mkconf $Id$
root@LinuxServer:~#

---

### Post by rubylaser on 2011-09-20
Are you using fakeraid or hardware raid for your mirror?  mdadm has no entries for arrays on this machine.  I think it has to be, because if you're wanting to do RAID5, your fdisk is only showing 2 disks in the whole machine.

---

### Post by DRouleau on 2011-09-20
Always forget that important part (sorry).  The RAID's are from a hardware RAID Controller, I want to say Perc 3i (it's a Dell Poweredge 2500).  If that part is important I can find out but I don't see where it would be.  The RAID 5 consists of 3 19.something GB disks.

---

### Post by DRouleau on 2011-09-20
I just rebooted the server and looked at the RAID Utility just to be sure and the 36.7 GB is the Mirror and the 36.4 is what it's saying for the RAID 5.  My main goal would be to get my share onto the RAID 5.

---

### Post by DRouleau on 2011-10-13
After a new installation of which I though I was using both drives still no luck.  This is the current output from fdisk -l:

Disk /dev/sda: 36.7 GB, 36698849280 bytes
255 heads, 63 sectors/track, 4461 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00062779

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4201    33739776   83  Linux
/dev/sda2            4201        4462     2096129    5  Extended
/dev/sda5            4201        4462     2096128   82  Linux swap / Solaris

Disk /dev/sdb: 36.4 GB, 36397645824 bytes
255 heads, 63 sectors/track, 4425 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005f15b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4426    35543041    5  Extended
/dev/sdb5               1        4426    35543040   83  Linux

---

### Post by DRouleau on 2011-10-13
Ok I think I have found something but I want to ask before I do it... can I change my Physical Volume to a Logical Volume or will I lose what is on the disks?

---

