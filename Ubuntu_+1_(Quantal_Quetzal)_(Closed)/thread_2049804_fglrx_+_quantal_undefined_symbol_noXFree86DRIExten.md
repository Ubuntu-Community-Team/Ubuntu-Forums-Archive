---
title: "fglrx + quantal: undefined symbol: noXFree86DRIExtension"
date: 2012-08-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by eudoxos on 2012-08-29
I downloaded fglrx from the ATI website (amd-driver-installer-12-8-x86.x86_64.zip[/CODE]) and applied patches (from [#993427]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/993427/comments/14")) to make the module compile with 3.4 and 3.5 kernels. DKMS modules compile fine, but when launching the X server, I am getting:

    ```
(EE) Failed to load /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so: undefined symbol: noXFree86DRIExtension

```

Is there a way around it? (I would use the open-source drivers, but those [don't work]("http://https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/1043328")).

---

### Post by jfernyhough on 2012-08-29
If you're running xserver 1.13rc (1.12.99) then the proprietary drivers won't work yet. You can downgrade to 1.12 and pin (or hold in Synaptic).

---

