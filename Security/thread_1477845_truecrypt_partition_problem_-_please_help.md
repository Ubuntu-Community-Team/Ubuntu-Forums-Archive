---
title: "truecrypt partition problem - please help"
date: 2010-05-09
forum: Security
---

### Post by ernest_francis on 2010-05-09
have a 1.5 gb hd, the whole disk is a truecrypt volume

now it seems to have got a bit messed up, this is what fdisk is reporting:

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003a80a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001   83  Linux
/dev/sdb2          182402      364802  1465136032+  83  Linux

When I go to select a device in truecrypt, it is saying:

/dev/sdb 1.4tb
/deb/sdb1 1.4tb
/dev/sdb2 2.5mb

Before there was no sdb1/sdb2 just /sdb , when I try and mount any of the volumes it says it is not a truecrypt volume or incorrect password

In gparted /dev/sdb is just a 1.36 unallocated volume

In TestDisk 6.11 I get the following info:

Disk /dev/sdb - 1500 GB / 1397 GiB - ATA SAMSUNG HD154UI

Hidden sectors are present.

size       2930277168 sectors
user_max   2930277168 sectors
native_max 18446744072344861488 sectors
dco        18446744072344861488 sectors
Host Protected Area (HPA) present.


Any idea what I can do to fix it - please help have lot of archived databases on here from previous projects so I need the data back

Yes I have a backup but its on dvd and would take ages to restore plus its in another country

thanks for any help in advance

---

