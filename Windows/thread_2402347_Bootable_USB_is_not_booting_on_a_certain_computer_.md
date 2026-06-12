---
title: "Bootable USB is not booting on a certain computer of mine that supports USB"
date: 2018-09-28
forum: Windows
---

### Post by s3a on 2018-09-28
The Windows installer doesn't boot on a certain computer, but it does boot on another one.

A USB Linux OS (Debian) does boot from that same computer.

The Windows installer boots on another computer.

Could someone please point me to something I can boot from, where what I boot from can tell my computer to boot the USB drive? Would that work?

Any help would be greatly appreciated!

---

### Post by oldfred on 2018-09-28
Which Windows?
UEFI or BIOS?
Windows 7 default is BIOS only, but you have to make some minor changes to make it UEFI bootable.
How you boot install media on newer UEFI systems is how it installs. So with UEFI Secure Boot off you should get two boot options, one UEFI and one just name/label of flash drive which is then a BIOS/CSM/Legacy boot. May also depend on whether UEFI has legacy boot on or off and if UEFI settings allow USB boot.
[http://www.rodsbooks.com/efi-bootloaders/secureboot.html](http://www.rodsbooks.com/efi-bootloaders/secureboot.html)
       Screenshots of secure boot settings Asrock, Asus, HP, Acer
[https://neosmart.net/wiki/disabling-secure-boot/](https://neosmart.net/wiki/disabling-secure-boot/)

---

