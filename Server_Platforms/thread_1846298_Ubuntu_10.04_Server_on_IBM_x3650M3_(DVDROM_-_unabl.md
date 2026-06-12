---
title: "Ubuntu 10.04 Server on IBM x3650M3 (DVDROM - unable to detect disks)"
date: 2011-09-18
forum: Server Platforms
---

### Post by jowoxx on 2011-09-18
Hi All,

I have installed ubuntu 10.04 server on an IBM x3650M3 server.
However, the DVDROM always detects CDs or DVDs in the drive as blank disk.

Is there anyway I can go around to resolve this?

Thanks!
Johnny

---

### Post by jowoxx on 2011-09-18
Example: I put a disk containing the Ubuntu Desktop 10.04 into the drive and sees a blank disk

[[IMG]http://s2.postimage.org/2jdf5f4ys/cdrom01.jpg[/IMG]]("http://postimage.org/image/2jdf5f4ys/")

I ran hwinfo --cdrom and it seems alright

# hwinfo --cdrom
46: SCSI 00.0: 10602 CD-ROM (DVD)                               
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_model_CDDVDW_TS_L633F
  Unique ID: KD9E.19Ss8EzA4q6
  Parent ID: w7Y8.k_mOZzYrMR7
  SysFS ID: /class/block/sr0
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
  Hardware Class: cdrom
  Model: "TSSTcorp CDDVDW TS-L633F"
  Vendor: "TSSTcorp"
  Device: "CDDVDW TS-L633F"
  Revision: "IT03"
  Driver: "ata_piix", "sr"
  Device File: /dev/sr0 (/dev/sg0)
  Device Files: /dev/sr0, /dev/block/11:0, /dev/scd0, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
  Device Number: block 11:0 (char 21:0)
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL, DVDRAM
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #36 (IDE interface)
  Drive Speed: 24

[URL="http://postimage.org/image/2jdf5f4ys/"][IMG]http://postimage.org/image/2jdf5f4ys/[/IMG]
[/URL]

---

