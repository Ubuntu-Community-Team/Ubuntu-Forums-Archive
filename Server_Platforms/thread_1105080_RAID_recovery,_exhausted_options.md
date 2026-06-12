---
title: "RAID recovery, exhausted options?"
date: 2009-03-24
forum: Server Platforms
---

### Post by delfering on 2009-03-24
I've been working for a number of days to recover the contents of four drives that a former system administrator set up. This was a log server and we somehow allowed the file system to fill up and the server refused to boot.

So the bottom line is that I need to mount at least the root file system volume and clear out some space.

The way that I've approached this is to boot from a live Desktop CD and use this tutorial:
[http://www.linuxjournal.com/article/8874](http://www.linuxjournal.com/article/8874)

Here are the detailed steps I've followed and the corresponding output. The LVM2 config file is attached to the message also.

Maybe I'm hosed and should just rebuild the whole thing, but if possible I'd like to recover these drives. Any help would be warmly appreciated. 

Thanks!

-----------------------------------------------------------

root@ubuntu:/home/delfering# sfdisk -l

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  60800   60801- 488384001   fd  Linux raid autodetect

Disk /dev/sdb: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0+  60800   60801- 488384001   fd  Linux raid autodetect

Disk /dev/sdc: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdc1   *      0+  60800   60801- 488384001   fd  Linux raid autodetect

Disk /dev/sdd: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdd1   *      0+  60800   60801- 488384001   fd  Linux raid autodetect

-------------------------------------

root@ubuntu:/home/delfering# mdadm --examine --scan /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 >> /etc/mdadm/mdadm.conf

The results of the edited /etc/mdadm/mdadm.conf file:
# This file was auto-generated on Mon, 23 Mar 2009 23:34:26 +0000
# by mkconf $Id$
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=c53de8fc:9567c38e:b282ff54:b4ee9e09 devices=/dev/sdb1,missing
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=462bb049:31641c37:7e08942a:eee5b6d9 devices=/dev/sda1,missing

-------------------------------------

root@ubuntu:/home/delfering# mdadm -A -s
mdadm: /dev/md1 has been started with 1 drive (out of 2).
mdadm: /dev/md0 has been started with 1 drive (out of 2).

-------------------------------------
At this juncture I used the dd command to examine the LVM2 header on the risk and then pare the gibberish out to hopefully come up with a 

working config file (which is attached to the forum message).

 vgcfgrestore -f nslog01b ns-log01
  Restored volume group ns-log01

--------------------------------------

root@ubuntu:/tmp# vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "ns-log01" using metadata type lvm2

---------------------------------------

root@ubuntu:/tmp# pvscan
  PV /dev/md0   VG ns-log01   lvm2 [465.76 GB / 465.76 GB free]
  PV /dev/md1   VG ns-log01   lvm2 [465.76 GB / 465.76 GB free]
  Total: 2 [931.52 GB] / in use: 2 [931.52 GB] / in no VG: 0 [0   ]

---------------------------------------

root@ubuntu:/tmp# vgchange ns-log01 -a y
  0 logical volume(s) in volume group "ns-log01" now active

--------------------------------------

root@ubuntu:/dev# vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "ns-log01" using metadata type lvm2

-------------------------------------

root@ubuntu:/home/delfering# pvdisplay
  --- Physical volume ---
  PV Name               /dev/md0
  VG Name               ns-log01
  PV Size               465.76 GB / not usable 1.44 MB
  Allocatable           yes
  PE Size (KByte)       4096
  Total PE              119234
  Free PE               119234
  Allocated PE          0
  PV UUID               fkqLOC-CKl1-vm1G-B4CO-g75j-rmkG-i4fAEy

  --- Physical volume ---
  PV Name               /dev/md1
  VG Name               ns-log01
  PV Size               465.76 GB / not usable 1.44 MB
  Allocatable           yes
  PE Size (KByte)       4096
  Total PE              119234
  Free PE               119234
  Allocated PE          0
  PV UUID               cORmdd-KQZm-UYzf-daTA-spN5-aV5p-1XNJWI

root@ubuntu:/home/delfering# vgdisplay
  --- Volume group ---
  VG Name               ns-log01
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  2
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                0
  Open LV               0
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               931.52 GB
  PE Size               4.00 MB
  Total PE              238468
  Alloc PE / Size       0 / 0
  Free  PE / Size       238468 / 931.52 GB
  VG UUID               XwNP3E-qcrL-YeMn-xD9u-BTBJ-Npsd-2orb53

--------------------------------------------------------

root@ubuntu:/home/delfering# lvscan
root@ubuntu:/home/delfering# 

-------------------------------------------------------

root@ubuntu:/home/delfering# /sbin/vgscan --mknodes
  Reading all physical volumes.  This may take a while...
  Found volume group "ns-log01" using metadata type lvm2
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper 1.02.27 (2008-06-25)(compat) and kernel driver

---

