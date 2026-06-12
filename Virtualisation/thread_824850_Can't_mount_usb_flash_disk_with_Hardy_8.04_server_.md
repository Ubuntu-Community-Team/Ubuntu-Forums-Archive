---
title: "Can't mount usb flash disk with Hardy 8.04 server xen kernel"
date: 2008-06-10
forum: Virtualisation
---

### Post by ralic on 2008-06-10
I'm trying to troubleshoot a problem with the 8.04 server xen kernel which fails to see my sata disk at boot time.

To seek help with that I'm trying to get the output of dmesg, but need to get it onto a usb flash disk and I can't get the flash disk to mount.

After being dropped to an initramfs prompt and inserting the flash disk, it is identified and a device /dev/sda is created with partition /dev/sda1, but when I try to mount it, I get:
```
mkdir /mnt
mount -t vfat /dev/sda1 /mnt
mount: Mounting /dev/sda1 on /mnt failed: No such device
```

Any ideas?

[Solution]
Ok, so basically the fat & vfat modules were not loaded into the kernel and needed to get loaded like so:
```
(initramfs) insmod /lib/modules/2.6.24-18-xen/kernel/fs/fat/fat.ko
(initramfs) insmod /lib/modules/2.6.24-18-xen/kernel/fs/vfat/vfat.ko

```
Thereafter the mount command worked fine.

Notes for future readers.
vfat module depends on fat module, so module load order is important.
Your modules version will likely differ from the 2.6.24-18-xen above. It's location likely wont, so a quick ls -l /lib/modules at the initramfs prompt will reveal it.
[/Solution]

---

