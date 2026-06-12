---
title: "usb-creator-gtk error on start"
date: 2021-03-31
forum: Ubuntu Development Version
---

### Post by corradoventu on 2021-03-31
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1922095](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1922095)
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1921910](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1921910)

---

### Post by dino99 on 2021-04-01
gir1.2-unity-7.0 has been removed some time ago while upgrading some packages. (probably 0.3.8)

usb-creator (0.3.8) groovy; urgency=medium

  * debian/control: Remove syslinux, syslinux-common, syslinux-legacy,
    genisoimage, mtools, parted Depends, they have not been required since
    0.3.0. Switch to Architecture: all since we no longer require syslinux.

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Tue, 18 Aug 2020 11:37:15 -0400

---

### Post by corradoventu on 2021-04-08
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1922095](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1922095) Fix released

---

