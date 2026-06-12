---
title: "Lemur Ultra SD card driver?"
date: 2013-02-02
forum: System76 Support
---

### Post by mysticalwhat on 2013-02-02
Hey everyone! I've installed the beta of Elementary OS on my Lemu4, and as much as I absolutely love my setup so far, I'm finding it difficult to cope with the fact that the System76 drivers don't work (regardless of the fact this is a subdistro of Ubuntu...). Do any of you have any suggestions? Standalone drivers? Hints to get it to work?

I'm not experienced with programming, so compiling my own set is way over my head. >_>

Please and thank you! :D

---

### Post by freechelmi on 2013-02-20
I guess your hardware is a Realtek Card Reader RTL8411 Device 5289

As explained here : 

[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/971876](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/971876)


You need to install the driver from realtek : 

[http://planet76.com/drivers/realtek/rts-bpp-dkms_1.1_all.deb](http://planet76.com/drivers/realtek/rts-bpp-dkms_1.1_all.deb)

Bundled as a dkms by system76.

For automount, the following line needs to be added to '/lib/udev/rules.d/80-udisks.rules'
DRIVERS=="rts_bpp", ENV{ID_DRIVE_FLASH_SD}="1"


This will work for SCCard, but inserting a MS sony card will crash your system, IMO this isssue is not fixed for now.

---

