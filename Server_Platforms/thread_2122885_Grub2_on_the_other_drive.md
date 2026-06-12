---
title: "Grub2 on the other drive"
date: 2013-03-06
forum: Server Platforms
---

### Post by cheshire mouse on 2013-03-06
Hi

I have several disks:
1 small disk (sda): 32Mb, can be set as a boot drive in BIOS
8 disks (sd[b-i]) attached through PCI SATA controller, BIOS knows nothing about them and can't boot OS from then

_Is there any way to make this system work WITHOUT placing /boot folder on the small disk_?

When I install ubuntu (12.04 server) all goes fine (raid creating, installation process, etc.) but grub doesn’t install MBR on sda. So system cant be loaded after reboot.
If i install MBR on sda manually, loading process ends with the grub rescue and **ls** command shows nothing except small disk

Need your opinions

---

