---
title: "ubuntu server in VirtualBox + vboxfs"
date: 2010-06-23
forum: Server Platforms
---

### Post by submute on 2010-06-23
Every time my kernel is upgraded (happens often), I reboot and forget to reinstall the VirtualBox guest additions, so my partitions in fstab that use vboxsf (for shared folders) are hosed.

Anyone devised a clever solution for this?

---

### Post by jbrown96 on 2010-06-23
DKMS is supposed to take care of external kernel modules during upgrades. See if you have it installed.

---

