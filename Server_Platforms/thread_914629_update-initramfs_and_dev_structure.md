---
title: "update-initramfs and /dev structure"
date: 2008-09-09
forum: Server Platforms
---

### Post by mariuss on 2008-09-09
For quite a while, after a kernel update, I keep getting these warnings every time there is a kernel update:
```
update-initramfs: Generating /boot/initrd.img-2.6.24-17-server
Warning: LBA32 addressing assumed
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/vg0/lvroot'
Warning: Name change: '/dev/dm-1' -> '/dev/vg0/lvtemp'
Warning: Name change: '/dev/dm-2' -> '/dev/vg0/lvswap'
Added Linux *
Added LinuxOLD
4 warnings were issued.
```

The system is working fine, but these warnings do worry me.

Does anyone know why they show up and what needs to be fixed?

---

### Post by mariuss on 2008-09-12
Until the last kernel update these warning were harmless. With the last one the server did not reboot anymore.

The system was eventually restarted by selecting LinuxOLD.

Forgot to mention in the previous message that LILO was installed for some reason, and I don't understant why. Every single Ubuntu install (both desktop and server) I have done in the past used GRUB. Under what circumstances is LILO installed?

Installing GRUB on top could fix the issue? How can GRUB be installed at this point?

---

### Post by mariuss on 2008-09-16
Figured why was LILO installed, because the root partition, /, is on LVM, and GRUB cannot read from LVM.

Ideally I should have put /boot on a separate partition, not on LVM, and then GRUB would have been installed.

It looks like LILO + LVM will break your system eventually. Not sure why during install you are given the option to partition everything with LVM.

Any suggestion on how could the system be fixed at this point, other that a complete reinstall, are more than appreciated.

---

