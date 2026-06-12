---
title: "Setting graphics to use VGA on boot instead of hdmi"
date: 2012-01-20
forum: Server Platforms
---

### Post by tr333 on 2012-01-20
I've got Ubuntu Server running on an ASRock A75M-HVS motherboard with AMD A8-3850 APU.  I can boot successfully when hdmi is connected, but I get a blank screen when I try to boot with the VGA connected instead of hdmi. How can I tell Ubuntu to use the VGA connection on boot instead of the hdmi connection?

---

### Post by tr333 on 2012-01-31
Fixed with a dodgy hack of disabling KMS on boot with "nomodeset".  If it was a full GUI system, that would force it into low graphics mode. :(

---

