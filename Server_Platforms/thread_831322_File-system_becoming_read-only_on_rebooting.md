---
title: "File-system becoming read-only on rebooting"
date: 2008-06-16
forum: Server Platforms
---

### Post by PseudoOne on 2008-06-16
Every time I reboot Ubuntu Server, No services can start or files be edited because it returns the error of "Read-only file system".  I do "touch fsck" and "exit" which makes it writable, but then it becomes read-only upon restart of the system.  When it is unwritable and I type "mount", the values for /dev/sda1 are:

(rw,errors=remount-ro).

Any help?

---

### Post by Titan8990 on 2008-06-16
What file format are you using?

---

