---
title: "GTB support for Ubuntu 9.10"
date: 2010-01-08
forum: Server Platforms
---

### Post by bikeman1 on 2010-01-08
I am installing a new large 4 Tb RAID (hardware) under 9.10.  Does GPT support come by default in the new 9.10 kernel?  How can I check?

I gather I need to use PARTED to make a GPT partition table on the raid.  

Anyone know details of how to do this?  Here is what I have found

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

---

### Post by bikeman1 on 2010-01-08
got my own answer .....install Gparted from synaptic, unmount the RAID device, run Gparted on this device and delete any existing partitions, use Gparted to install a new partition table <<of type GPT>>, install a new partition(s) here, and format the partition(s) as ext3, all within Gparted.  Worked fine.  Fdisk will not see the partitions correctly after the GPT partition is installed.   Will have to use Gfdisk or something

Ext3 partitions will take an hour or more to install and verify (4Tb).  

clearly the 9.10 kernel has GPT support built in.  The web information I had found was correct but dated on this.

---

### Post by CharlesA on 2010-01-08
Indeed. It does support GPT, but you cannot create GPT partitions with fdisk, you need to use gparted. :)

> **bikeman1 said:**
> Fdisk will not see the partitions correctly after the GPT partition is installed.

Huh?

Mine displays fine:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: The size of this disk is 4.0 TB (4000627818496 bytes).
DOS partition table format can not be used on drives for volumes
larger than (2199023255040 bytes) for 512-byte sectors. Use parted(1) and GUID
partition table format (GPT).


Disk /dev/sdb: 4000.6 GB, 4000627818496 bytes
255 heads, 63 sectors/track, 486381 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000


```

---

