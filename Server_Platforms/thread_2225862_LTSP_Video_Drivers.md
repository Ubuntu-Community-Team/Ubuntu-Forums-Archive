---
title: "LTSP Video Drivers"
date: 2014-05-23
forum: Server Platforms
---

### Post by imotor on 2014-05-23
I need to run HP t510 thin clients from an Ubuntu 12.04 LTSP server. These clients use the VIA chipset and unfortunately the OpenChrome driver is worthless for DVI video. If I boot Ubuntu 12.04 directly from the t510 and install the driver from VIA, the video works great. 

I tried installing LTSP directly on the t510 thin client, then installing the VIA driver into the LTSP chroot, and copying the chroot to the main LTSP server. But now the client doesn't boot past the Ubuntu logo; it goes through an endless loop of the Ubuntu logo and progress dots.

Could the problem be that the new driver is not installed in the initramfs?

Any ideas?

Thanks.

---

