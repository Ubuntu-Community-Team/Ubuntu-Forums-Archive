---
title: "Dual booting Windows 7 on Kudu"
date: 2017-10-28
forum: System76 Support
---

### Post by pa786c on 2017-10-28
I have Ubuntu 16.04 and want to install Win7 for a dual-boot setup. I've created a 100Gb NTFS partition, disabled secure UEFI booting, and booted with Windows 7 USB (knowing I will have to repair GRUB). I got the attached blue screen of death....what's going on? Do I need to recreate the Windows 7 USB in a different way?

[http://i.imgur.com/b2iKtt3.jpg](http://i.imgur.com/b2iKtt3.jpg)

---

### Post by jw-bloodworth on 2017-10-30
in the BOIS check the power settings and see how they are configured.

---

### Post by pa786c on 2017-10-31
below I linked to an album of each BIOS screen.

To get the system to recognize the bootable USB key, I have to change the UEFI boot to DISABLE on the second-to-last screen.

[https://imgur.com/a/dXvKq](https://imgur.com/a/dXvKq)

---

