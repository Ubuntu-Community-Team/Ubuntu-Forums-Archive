---
title: "IBM X3550 and SAS Hard Drives"
date: 2008-11-05
forum: Server Platforms
---

### Post by CamboCambo on 2008-11-05
Hi,

I am installing on an IBM X3550 with 2 73gb SAS hard drives, they are in a RAID 1 array.  I boot off the CD and the installation works ok, the installer can see the hard disks and I partition them and set a boot partition active. the installation completes without a hitch.

The issue comes at the reboot, I see the bios, then the RAID controller starts then nothing, small white _ flashing in the top right of the screen.  It is as though it isnt loading any boot loader.

I have checked the bios and my boot order is correct and I have checked that my RAID mirror is active (can be booted from)

I have tried 8.04 i386, 8.10 i386 and 8.10 x64 with the same results.

Any Ideas??

Thanks

---

### Post by CamboCambo on 2008-11-05
I have just installed a copy of RHEL 5.1 with no changes to the RAID array config or BIOS and it will boot.  Not my desirable outcome however this does tell me that my hardware config does work.

---

### Post by Thomaskj on 2008-12-08
I have just experienced the same with Ubuntu Server 8.10.

---

### Post by Thomaskj on 2008-12-08
Ubuntu Server 64bit 8.04 works.

---

