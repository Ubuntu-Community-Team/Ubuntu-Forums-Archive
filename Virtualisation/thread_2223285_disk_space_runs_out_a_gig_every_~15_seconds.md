---
title: "disk space runs out a gig every ~15 seconds"
date: 2014-05-10
forum: Virtualisation
---

### Post by areblitz on 2014-05-10
Hi,

I installed ubuntu 13.10 onto my laptop on an SSD (256Gb), then downloaded vmware workstation trial (with a view to purchase, if it suits my purpose)....everything went well so far, however, whilst working in the vm after a while....I noticed that my disk space was running out at a rate of 1gig / ~15 seconds. Anyone ever seen this before? (the OS is using encryption...which I don't know much about), but surely there is one other ubuntu users who has an SSD and installed win7 via vmware workstation that might know what's going on.

have tried to search with no luck here.

Thanks
Adam

update: looks like there was an issue with "enable write cache" and scsi hard drive. Have changed to SATA and unticked the box for "enable write cache".

---

