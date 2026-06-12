---
title: "Mounting large (12TB) SCSI attached RAID array (formatted with ntfs) in ubuntu server"
date: 2010-02-16
forum: Server Platforms
---

### Post by djotanov on 2010-02-16
Hi,
I have a large RAID array of 12 TB attached to one of my Ubuntu server machines. The RAID volume is formatted with NTFS. The problem is that I can not mount this volume in Ubuntu. I can read it normally if I attach it to windows machine. 

This is the output from "sudo fdisk -l":
sudo fdisk -l

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff383517

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7266    58364113+   7  HPFS/NTFS
/dev/sda2            7267       20022   102462570    f  W95 Ext'd (LBA)
/dev/sda5            7267       20022   102461440    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x163ed396

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18657   149862321   83  Linux
/dev/sdb2           18658       19452     6385837+   5  Extended
/dev/sdb5           18658       19452     6385806   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.

Note: sector size is 4096 (not 512)

WARNING: The size of this disk is 12.0 TB (11999999164416 bytes).
DOS partition table format can not be used on drives for volumes
larger than (17592186040320 bytes) for 4096-byte sectors. Use parted(1) and GUID 
partition table format (GPT).


Disk /dev/sdc: 12000.0 GB, 11999999164416 bytes
256 heads, 63 sectors/track, 181652 cylinders
Units = cylinders of 16128 * 4096 = 66060288 bytes
Disk identifier: 0xdfdb4445

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      266306  4294967292   ee  GPT


I am trying to mount /dev/sdc :
sudo mount -t ntfs-3g /dev/sdc /mnt/aberdeen/
NTFS signature is missing.
Failed to mount '/dev/sdc': Invalid argument
The device '/dev/sdc' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

or:
sudo mount -t ntfs-3g /dev/sdc1 /mnt/aberdeen/
ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2009 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)


I am a relative newbie in Linux world so I would appreciate if someone could give me an advice how to solve this.

---

### Post by japsai on 2010-02-16
Try 

```
ls -a /dev
```

---

### Post by joberly on 2010-02-16
Try viewing your drives using gparted. It seems that is the tool to use when talking about > 2TB filesystems.

EDIT: There are also some good resource at the bottom of [this]("http://www.ibm.com/developerworks/linux/library/l-gpt/")[ibm.com] page.

---

