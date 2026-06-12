---
title: "set uas module parameter"
date: 2022-04-12
forum: Server Platforms
---

### Post by bjlockie on 2022-04-12
This was on my desktop.
I was trying to figure out why smartctl didn't work on my usb hard drive.

I tried to disable uas and NO_ATA_1X as per:
[https://www.smartmontools.org/wiki/SAT-with-UAS-Linux](https://www.smartmontools.org/wiki/SAT-with-UAS-Linux)
 by creating /etc/modprobe.d/disable_uas.conf:
# disable uas for 0bc2:ac30 Seagate RSS LLC BUP Slim
options usb_storage quirks=0bc2:ac30:u
that didn't work so I modified the GRUB command line in /etc/default/grub
GRUB_CMDLINE_LINUX="iommu=soft audit=0 usb_storage.quirks=0bc2:ac30:"

It works with uas and the NO_ATA_1X flag on my desktop by modifying grub.

I want to get it working on my raspberry pi running ubuntu server.
The modprobe.d file doesn't work and I don't think it uses grub.

How do I add a storage.quirk to the boot cmd line of ubuntu server?

---

### Post by bjlockie on 2022-04-18
I added usb-storage.quirks=0bc2:ac30:u to /boot/firmware/cmdline.txt and did update-initramfs (I don't know if I needed to).

---

