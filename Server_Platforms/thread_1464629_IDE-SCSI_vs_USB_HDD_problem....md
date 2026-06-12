---
title: "IDE-SCSI vs USB HDD problem..."
date: 2010-04-28
forum: Server Platforms
---

### Post by mslovette on 2010-04-28
I have 9.10 server loaded, with an internal ADAPTEC IDE-SCSI array configured and operational as a main repository for SAMBA-managed data. Recently, I connected an external USB-HDD for backup purposes, configured it at the command line and used it for the purpose that I intended, and all was well.. until...
 
I left the USB HDD powered and connected with no permanent entry in fstab. Upon reboot, I discovered that the USB drive snatched up the /dev entry for the RAID and then mounted it AS the RAID, causing my heart to stop beating... well, for only a moment.
 
Once I figured out what was wrong I was able to re-mount my RAID. However my problem remains. How can I be assured that, upon every boot, my USB HDD will not usurp the RAID /dev assignments?
 
any assistance will be greatly appreciated.
 
==============================
 
UPDATE: Have altered the fstab file such that my RAID is identified by UUID vice the name supplied at bootup. This 'appears' to have solved my problem... but I'd like to be (reasonably) sure that this is not going to come back to bite me at some future date. -mslovette-

---

