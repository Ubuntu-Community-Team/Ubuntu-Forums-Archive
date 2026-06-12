---
title: "Marry to Hardware"
date: 2008-03-18
forum: Security Discussions
---

### Post by picopir8 on 2008-03-18
Does anyone know of a way to merry an install to a particular hardware configuration (much like how windows restore disks only work on certain computers).  I want to put an install on a USB drive but then lock the drive so it will only boot off one computer.

---

### Post by ajgreeny on 2008-03-18
I think if you do a normal install of Ubuntu to an external usb drive as if it were an internal drive, and not as a live usb external system, it will only boot on the machine which you used to install it.  This is probably because the grub menu will not recognise the partitions etc if it is booted (or rather tried to boot) on another machine.

Someone correct me if I'm wrong please.

---

