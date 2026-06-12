---
title: "[SOLVED] Boot fail, initramfs prompt."
date: 2016-09-05
forum: Ubuntu Studio
---

### Post by Matthew_Abd-El-Aha on 2016-09-05
Apologies for lack of details but upon googling something along the lines of "ubuntu boot fail initramfs" and finding hundreds upon hundreds of posts concerning this error dating since version 12.04 with often very lengthy solutions I fixed mine just with

*fsck /dev/sda6* 
(sda6 being my errored partition)

I checked "y" to fix each error and then rebooted. Everything is working fine now.

---

