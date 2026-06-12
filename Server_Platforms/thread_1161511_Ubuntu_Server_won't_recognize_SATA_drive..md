---
title: "Ubuntu Server won't recognize SATA drive."
date: 2009-05-16
forum: Server Platforms
---

### Post by Nixie Pixel on 2009-05-16
During initial installation, Ubuntu Server 8.10 told me that it could not initialize my SATA hard drive (it wanted me to turn on SATA RAID to recognize the drive, even though the SATA port is not a RAID controller as far as I know).

fdisk can't see the drive, either.  It is available in BIOS. 

How can I get Ubuntu Server to recognize the drive?

Thanks!

---

### Post by cariboo on 2009-05-16
DO you have a setting for AHCI, or emulation mode in the BIOS? Try the ACHI setting if you have it.

---

### Post by Nixie Pixel on 2009-05-16
Actually, nevermind, it seems there was a problem with the SATA controller itself.  I plugged it into another controller and I could see it in fdisk.

Thanks!

---

