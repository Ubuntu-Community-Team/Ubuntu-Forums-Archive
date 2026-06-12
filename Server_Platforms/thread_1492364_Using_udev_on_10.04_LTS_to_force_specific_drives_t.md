---
title: "Using udev on 10.04 LTS to force specific drives to keep specific device names"
date: 2010-05-24
forum: Server Platforms
---

### Post by nerr on 2010-05-24
I recently added a Sans Digital TR4M-B 4-bay eSATA RAID enclosure to my home server, which is a 4-bay Acer easyStore H340 running Ubuntu 10.04 LTS.  As a result of adding the TR4M-B, my device names are never persistent between reboots, which can be incredibly aggravating at times.  It's quite a pain when your operating system drive shows up as /dev/sde and your external hard drive is in /dev/sda.  I typically use UUIDs to mount drives and in /etc/fstab and such, but I would still like to find a way to keep these names persistent so that I can use tools such as smartmontools automatically to check my drives by device name.

Here are the devices attached to the machine, and the names which I would like them to have if possible.

Internal Drives:
WDC WD10EADS-00L5B1 (/dev/sda)
WDC WD10EAVS-00D7B1 (/dev/sdb)
WDC WD6400AACS-00D6B1 (/dev/sdc)
WDC WD10EARS-00Y5B1 (/dev/sdd)

External Drive:
ST315003 41AS (/dev/exthdd0 OR /dev/sde)

Misc: (built-in 256MB flash chip inside machine, which I don't use)
SMI USB Disk: (/dev/usbdisk0 OR /dev/sdf)

Any guides which I've read through about udevadm and udev in general seem terribly out of date, and I don't know enough to improvise my own solution.  If anyone could point me in the right direction, it would be much appreciated.

---

### Post by redmk2 on 2010-05-24
> **nerr said:**
> I recently added a Sans Digital TR4M-B 4-bay eSATA RAID enclosure to my home server, which is a 4-bay Acer easyStore H340 running Ubuntu 10.04 LTS.  As a result of adding the TR4M-B, my device names are never persistent between reboots, which can be incredibly aggravating at times.  It's quite a pain when your operating system drive shows up as /dev/sde and your external hard drive is in /dev/sda.  I typically use UUIDs to mount drives and in /etc/fstab and such, but I would still like to find a way to keep these names persistent so that I can use tools such as smartmontools automatically to check my drives by device name.

Here are the devices attached to the machine, and the names which I would like them to have if possible.

Internal Drives:
WDC WD10EADS-00L5B1 (/dev/sda)
WDC WD10EAVS-00D7B1 (/dev/sdb)
WDC WD6400AACS-00D6B1 (/dev/sdc)
WDC WD10EARS-00Y5B1 (/dev/sdd)

External Drive:
ST315003 41AS (/dev/exthdd0 OR /dev/sde)

Misc: (built-in 256MB flash chip inside machine, which I don't use)
SMI USB Disk: (/dev/usbdisk0 OR /dev/sdf)

Any guides which I've read through about udevadm and udev in general seem terribly out of date, and I don't know enough to improvise my own solution.  If anyone could point me in the right direction, it would be much appreciated.
It appears that you are using a single partition per drive (i.e. *WDC WD10EADS-00L5B1 (/dev/sda)*.  You can also use partition labels instead of UUID's for this purpose.  See [**_here _**]("WDC WD10EADS-00L5B1 (/dev/sda)")or [**_here_**]("http://www.linuxconfig.org/how-to-label-hard-drive-partition-under-linux") for more info.

---

