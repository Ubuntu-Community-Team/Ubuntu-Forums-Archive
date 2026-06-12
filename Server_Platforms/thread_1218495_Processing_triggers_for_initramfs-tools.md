---
title: "Processing triggers for initramfs-tools"
date: 2009-07-20
forum: Server Platforms
---

### Post by novenobit on 2009-07-20
hello ubuntu users, i have a problem with my server and i cant solve it with: **_sudo dpkg --configure -a _**
this is what i get when i run this command:

Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-13-server
cpio: ./lib/klibc-*.so: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-13-server
dpkg: subprocess post-installation script returned error exit status 1

i have check this forum, found no solution
could someone help me here,

---

