---
title: "LTSP-Install video driver in chroot?"
date: 2013-12-02
forum: Server Platforms
---

### Post by imotor on 2013-12-02
I have an amd64 Ubuntu 12.04 LTSP server with an amd64 image for LTSP.

I am trying to get HP t510 thin clients to boot with dual displays over DVI at 1920x1080.

The HP t510 has a VIA VX900/Chrome9 chipset. The openchrome driver included in 12.04 doesn't auto-detect displays, so no DVI, dual displays or resolution above 1024x768.

I have downloaded the VIA driver from [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) and tried logging into the LTSP chroot, uninstalling the openchrome driver, but I cant get the VIA driver to install because its install script searches for the VIA chipset connected to the system, which it obviously doesn't find.

Is there a way to get the LTSP chroot to talk to the HP thin client so I can install the VIA driver?

Thanks.

---

### Post by imotor on 2013-12-05
Should I install the driver on another client and copy the files over to the chroot?

---

