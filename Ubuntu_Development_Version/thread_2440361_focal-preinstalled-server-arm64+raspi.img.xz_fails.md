---
title: "focal-preinstalled-server-arm64+raspi.img.xz fails to boot (initrd.img/vmlinuz)"
date: 2020-04-09
forum: Ubuntu Development Version
---

### Post by ububob2 on 2020-04-09
For the last few days the 'current' ubuntu-server image for Raspberry Pi (focal-preinstalled-server-arm64+raspi.img.xz) fails to boot as the
initrd.img and vmlinuz files are missing from the system-boot partition within the image.


Please can someone point me to the right place where I can check if this has already been reported, or where I can report the problem?


Thanks an lot.

---

### Post by ububob2 on 2020-04-09
Just to clarify the 'current' daily-preinstalled version at:

[http://cdimage.ubuntu.com/ubuntu-server/daily-preinstalled/current/focal-preinstalled-server-arm64+raspi.img.xz](http://cdimage.ubuntu.com/ubuntu-server/daily-preinstalled/current/focal-preinstalled-server-arm64+raspi.img.xz)

has the problem, but the 20.04 beta release at:

[http://cdimage.ubuntu.com/releases/20.04/beta/ubuntu-20.04-beta-preinstalled-server-arm64+raspi.img.xz](http://cdimage.ubuntu.com/releases/20.04/beta/ubuntu-20.04-beta-preinstalled-server-arm64+raspi.img.xz)

does not. The initrd.img and vmlinuz are present in the beta version.

---

