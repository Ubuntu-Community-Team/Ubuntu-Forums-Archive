---
title: "Upgrading hanging during &quot;generating grub configuration file&quot;..."
date: 2014-03-29
forum: Ubuntu Development Version
---

### Post by Sslaxx on 2014-03-29
I noticed that upgrading to kernel 3.13.0-20 on here the process appears to halt at the grub configuration stage, more specifically at

> Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-20-generic
Found initrd image: /boot/initrd.img-3.13.0-20-generic
Found linux image: /boot/vmlinuz-3.13.0-19-generic
Found initrd image: /boot/initrd.img-3.13.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin

EDIT: It appears that the process was hanging because the external hard drive hadn't been mounted properly... Has anyone else been having this issue?

---

### Post by bedas on 2014-09-18
exactly same issue here, resolved by unmouting a nfs share (nfs server was under maintenance)

---

### Post by cariboo on 2014-09-18
Thread closed, as it has nothing to do with utopic.

---

