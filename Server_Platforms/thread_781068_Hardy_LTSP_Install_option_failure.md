---
title: "Hardy LTSP Install option failure"
date: 2008-05-04
forum: Server Platforms
---

### Post by bodycoach2 on 2008-05-04
One several machines I've tried, I followed the instructions:
After selecting language at startup, press F4, and select LTSP option.

I get all the way to the end where it installs the LTSP system (LTSPchroot)- and it fails on each installation. This has happened on several machines. Is there a bug, and if so, is there a workaround? Or, am I doing something wrong (like following instructions?)

---

### Post by bodycoach2 on 2008-05-04
Problem fixed. MD5 checksum was okay on the first disk, and disk integrity check out fine, but LTSP chroot wouldn't install. One the second one, everything installed.

I used GnomeBaker on the second disk, instead of Brasero.

---

