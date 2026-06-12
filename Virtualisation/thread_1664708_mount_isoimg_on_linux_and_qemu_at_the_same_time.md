---
title: "mount iso/img on linux and qemu at the same time"
date: 2011-01-11
forum: Virtualisation
---

### Post by AGSzabo on 2011-01-11
hi,

this is a general qemu question: is it save to have the boot.img image mounted on linux side while using it in qemu? no? but is it save to have the .iso mounted on linux side while qemu has inserted it as 'cdrom'?

an then, i need two commands on linux side to mount the boot.img. one is a losetup:

losetup -o 32256 /dev/loop0 BOOT.img

and the other is the mount:

sudo mount /dev/loop0 /media/temp

but when umnounting the boot.img, is it enough to make an umount or must i do also a losetup -d?

---

