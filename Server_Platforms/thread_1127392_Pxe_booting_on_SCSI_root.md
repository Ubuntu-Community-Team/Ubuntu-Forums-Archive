---
title: "Pxe booting on SCSI root"
date: 2009-04-16
forum: Server Platforms
---

### Post by blopeur` on 2009-04-16
Hi,

i am currently trying to pxe boot on an ISCSI partition.

I can install fine the root  system either directly on the iscsi system or by doing local HD , then DD to the ISCSI. 

Configuring teh dhcp + tft to push a kernel to pxe boot, works fine too 

However i start having issue on how to create the initramfs and the kernel + how to configure the dhcp / tftp etc.. so the iscsi get mounted at boot.

Anybody got an idea or a link to a nice tutorial? 

I ve tried different solution (gpxe, and other) but they all seems to fail

---

