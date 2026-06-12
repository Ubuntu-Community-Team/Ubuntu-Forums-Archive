---
title: "Slightly OT: Making a Windows/DOS boot floppy under Linux"
date: 2005-05-17
forum: The Cafe
---

### Post by valthonis on 2005-05-17
I know this is probably the wrong forum for this, but I couldn't find anyplace else that made any sense to post in.  I have an old server board (Tyan Tiger 100) running Hoary, but it's got an ancient BIOS dating from 1997.  The manufacturer issued the latest BIOS back in 2001 which features a lot of fixes I'd like to have, but since it's an old board it requires a Win/DOS boot disk to flash the BIOS.  I've been scouring the net via Google and other search engines looking for ways to obtain a compatible boot floppy image and write it to floppy via **dd**.  I found a few at [bootdisk.com](http://www.bootdisk.com) , but attempts to write the images there to disk result in my system getting stuck in dd for hours.  This is the command I've been using:
```
dd if=/path/to/boot.img of=/dev/fd0 bs=1440k count=1
```
Does anyone have any insight on this?  Thanks in advance.

---

### Post by nad on 2005-05-17
Leave out the bytes per sector and count arguments, this is clearly wrong.

Why not just use a freedos disk? freedos.org

---

### Post by valthonis on 2005-05-20
Thanks, Nad.  I determined that the floppy drive was malfunctioning.  A replacement drive and your corrected command worked wonders.

---

