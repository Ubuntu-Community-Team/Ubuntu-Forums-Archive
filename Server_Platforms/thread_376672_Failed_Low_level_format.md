---
title: "Failed Low level format"
date: 2007-03-05
forum: Server Platforms
---

### Post by mark458 on 2007-03-05
OK so Im on a dell poweredge 2650 the bios has a low level format option in it I decided I would for mat all 5 drives because I had just bought the unit. I low leveled 2 drives and they both failed gave a weird error after that windows setup would no longer access the drive. Regular windows formating of the other drives took 24 hours... Now what can I do with ubuntu without installing it to check the drives on this server?

---

### Post by Mr. C. on 2007-03-05
Drives are typically factor checked and ready for a file system.  Using the low-level formatting tools provided by 3rd parties are often suboptimal.  Rarely do you need to perform such.

See if the disk mfg. has formatting tools.  Use their tools if they exist.   They will often have tools to read the SMART information.

You can boot with a live gpartd CD and format:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

See if this helps,
MrC

---

