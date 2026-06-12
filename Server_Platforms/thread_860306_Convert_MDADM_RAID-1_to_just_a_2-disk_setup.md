---
title: "Convert MDADM RAID-1 to just a 2-disk setup"
date: 2008-07-15
forum: Server Platforms
---

### Post by TheGameAh on 2008-07-15
Hi guys.

Have (2) 80 gig drives setup in RAID1 software mirror.  This server is just a VMWare server hosting a few machines.  Not real intensive.  Turns out I don't really need the RAID so much.  I could rebuild the server quickly, and would rather use the second drive to have a backup of the VMs, which would then be copied to tape drive.  

I could move the VMs, rebuild the server, then move them back.  But I was wondering if there was a pain-free way to break the mirror, keeping the data on the first drive, and just convert it to a 2 disk setup.

---

### Post by windependence on 2008-07-16
I would make a backup copy of the VMs on another drive, DVD, flash media or anywhere OTHER than the two drives, then wipe both drives using something like a dd script and reinstall a fresh os, and VMware and move your VMs back in. In any case make a backup of the VMs anyway, you never know.

-Tim

---

