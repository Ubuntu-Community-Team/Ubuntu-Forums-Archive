---
title: "Can't mound Nikon D80 in 8.04, but it mounts fine in WinXP running in VB"
date: 2009-02-02
forum: Ubuntu Studio
---

### Post by vancouverite on 2009-02-02
Hi,
I have a Nikon D80 that won't mount in Ubuntu.  I have tried restarting with the camera attached, and installing autofs, both to no avail.

The curious thing is that when I run WinXP in Virtual Box it mounts the camera just fine.  So I know it is connected and the system can see it (it shows up in lsusb), but Ubuntu won't use it.

Any ideas?

Van

---

### Post by DominaDoom on 2009-02-08
I can't mount my D80 in 8.10.  Nothing I've tried will detect the camera or my card reader.

---

### Post by thorgal on 2009-02-09
same thing here. What I will do is buy a card reader than can read/write on SDHC (or high capacity SD). The SD only card reader cannot handle SDHC because the damn SDHC is not backward compatible. What a waste ...

---

### Post by POWMS on 2009-02-09
Van
I have a Nikon D40 that would not mount in Xubuntu 8.04.
Due to other issues I installed Xubuntu 8.10 and the D40 mounts instantly when connected, as a mass storage device.
If I still used 8.04 I would have purchased a usb card reader to resolve this.

---

### Post by DominaDoom on 2009-04-25
I'm running Jaunty now, and there is no D80 detection in PTP or Mass Storage.  I would like to learn to write a driver.  I am a semi professional photographer, and I won't go back to using Adobe anytime soon.

---

### Post by vancouverite on 2009-04-29
Hi all,
I figured this one out and got the D80 to connect.  According to the libgphoto2 [website]("http://www.gphoto.org/proj/libgphoto2/support.php") the camera only works in PTP (Picture Transfer Protocol) mode.  I changed the camera's USB settings to *MTP/PTP* and ubuntu saw it right away.

Cheers,
Van

---

