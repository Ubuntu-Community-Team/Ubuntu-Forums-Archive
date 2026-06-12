---
title: "LSI Logic 53C8XX PCI SCSI host adapter driver"
date: 2010-05-25
forum: Server Platforms
---

### Post by beckzar on 2010-05-25
I'm trying to attach an HP StorageWorks Ultrium LTO4 Tape driver to a server running Ubuntu Server 10.04 LTS. The HBA controller needs the following modules/drivers:

**st** - The tape driver. 
**sym53c8xx** - The SCSI chipset driver for the LSI Logic family of HBAs
**aic7xxx** - The SCSI chipset driver for the Adaptec 7xxx chipset family

It's present in the desktop version using **sudo modprobe -l | grep "sym"**.
However, on Ubuntu Server 10.04 LTS I can't find the **sym53c8xx** module.

How do I get and install that module into Ubuntu Server 10.04?

Thanks!

---

