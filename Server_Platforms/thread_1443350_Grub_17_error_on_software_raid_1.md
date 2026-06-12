---
title: "Grub 17 error on software raid 1"
date: 2010-03-31
forum: Server Platforms
---

### Post by CyberCowboy on 2010-03-31
I've got a software raid 1 happening including /boot and am getting a grub 17 error.  I can't seem to boot into the rescue system from a live disk because it can't load both disks of the raid.  Any help greatly appreciated

If it matters this is on 9.04

---

### Post by CyberCowboy on 2010-04-02
I rebuilt the box using 10.04

---

### Post by fang0654 on 2010-04-02
It was a software bug in Grub 2.  Glad to see it is fixed (I had to patch the binaries on a server I had to get it to work).

Another workaround is to connect a floppy drive.  Doesn't need any actual floppies, just a drive.

---

