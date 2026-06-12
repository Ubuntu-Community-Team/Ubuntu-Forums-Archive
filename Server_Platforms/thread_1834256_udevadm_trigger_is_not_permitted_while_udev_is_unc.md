---
title: "udevadm trigger is not permitted while udev is unconfigured"
date: 2011-08-27
forum: Server Platforms
---

### Post by bortred on 2011-08-27
Hi All

I'm having a bit of a nightmare with my ubuntu hardy server (using hardware raid 1+0). Following a power cut I get the message "udevadm trigger is not permitted while udev is unconfigured" on boot.  Before the power cut the server had been up for ~450 days.

I managed to get access to /boot (which was empty) by using the repair option on the alternate cd and mounting /dev/myserver/root. I've installed the packages linux-headers-server, linux-image-server and linux-server. The various 2.6.24-29 files were installed and update-initramfs was automatically run (I noticed others have used update-initramfs to solve this error when upgrading from 8.04 to 10.04 in some posts I've read). No luck with this though - just the same error booting.  I've also tried reinstalling udev, but again with no success.

I rebooted and pressed the Esc key to get the boot menu up. Only options were for kernel 2.6.24-26 (rather than the 2.6.24-29 just installed). I ran the recovery option anyway and got "/dev/mapper/myserver-root does not exist".

Does anyone have ideas how to solve this (be it by repairing this or upgrading to 10.04 lts without losing data, or whatever)? Any help/advice appreciated.

Thanks

b

---

### Post by bortred on 2011-08-31
Gave up.  Mounted root partition using rescue disk and copied data over.  Installed ubuntu 10.04 lts.

---

