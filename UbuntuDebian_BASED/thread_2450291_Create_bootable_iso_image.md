---
title: "Create bootable iso image"
date: 2020-09-10
forum: Ubuntu/Debian BASED
---

### Post by piotrm2 on 2020-09-10
Hi

KDE Neon bases on Ubuntu (Ubuntu focal 20200907-19:10) and its live version supports casper file system, so theoretically is possible to save changes in pendrive where system is stored. To make this works well, among other, needs to add in boot configuration (grub.cfg) to any menu entry option 'persistent', which normally is missing and may looks like below:

> menuentry "KDE neon persistent" {
load_video
set gfxpayload=keep
linux<->/casper/vmlinuz boot=casper **persistent** apparmor=0 quiet splash ---
initrd<>/casper/initrd
}

To avoid modifying grub.cfg file in case of every boot of KDE Neon from pendrive I tried to recreate iso (one cannot modify iso, because this is read only file system) with properly updated grub.cfg file. 
I prepared several bootable iso images. I have put it each time on pendrive (by dd commnad) and tried to boot my laptop. Unfortunately from unknown (for me) reason it didn't want to boot from my Lenovo ThinkPad T480 (originally here is installed Windows 10 business edition). Please notice that originally downloaded iso of KDE Neon, which was stored into pendrive in the same way (by dd), just booting in this laptop without any problem. Additionally my every images were for sure bootable, because they were boot on different machine, like Toshiba Portage (~7 years old laptop), where is present only different Linux distribution.

I wonder if anyone met such problem and solved it so could help me?

To create bootable iso image I followed instruction I found here: [https://wiki.syslinux.org/wiki/index.php?title=Isohybrid](https://wiki.syslinux.org/wiki/index.php?title=Isohybrid)
Therefore I created image for BIOS, UEFI and mixed like this

> 
xorriso -as mkisofs -o neon-developer-20200907-1848-1.iso -isohybrid-mbr /usr/lib/syslinux/bios/isohdpfx.bin -c isolinux/boot.cat -b isolinux/isolinux.bin -no-emul-boot -boot-load-size 4 -boot-info-table neon-developer-20200907-1848-1


---

### Post by QIII on 2020-09-10
Moved to Ubuntu/Debian BASED

---

### Post by scdbackup on 2020-09-11
Hi,

your xorriso run does not mark EFI boot equipment, but only the software
for booting via BIOS. You probably need to do what is described in
  [https://wiki.syslinux.org/wiki/index.php?title=Isohybrid#UEFI](https://wiki.syslinux.org/wiki/index.php?title=Isohybrid#UEFI)

About repacking Debian (and current Ubuntu) ISOs, see
  [https://wiki.debian.org/RepackBootableISO](https://wiki.debian.org/RepackBootableISO)
and since there is no /.disk/mkisofs file in Ubuntu ISOs
  [https://wiki.debian.org/RepackBootableISO#What_to_do_if_no_file_.2F.disk.2Fmkisofs_exists](https://wiki.debian.org/RepackBootableISO#What_to_do_if_no_file_.2F.disk.2Fmkisofs_exists)

Have a nice day :)

Thomas

---

### Post by sudodus on 2020-09-11
I downloaded and tested the current 'user edition' [FONT=Courier New]**neon-user-20200910-0945.iso**[/FONT]

and used [mkusb](https://help.ubuntu.com/community/mkusb) (mkusb-dus) to create a persistent live drive.

Since this is not a standard Ubuntu system, I tried with the setting 'usb-pack-efi', and it works out of the box (no tweaks except 'usb-pack-efi') both in BIOS mode and in UEFI mode.

---

### Post by C.S.Cameron on 2020-09-11
Was that old or new 'usb-pack-efi'?

---

### Post by sudodus on 2020-09-12
I tested with the new default 'usb-pack-efi' of mkusb version 12.6.0 (now at ppa:mkusb/unstable).

Sorry, I did not test with mkusb version 12.5.8 from the stable PPA, ppa:mkusb/ppa. I tested now, and the persisstent live KDE-Neon works in BIOS mode and in UEFI mode also with this version of mkusb (mkusb-dus)

[hr][/hr]
Comments:

1. mkusb's grub system needs version 12.6.0 to boot with secure boot in computers with the *fix for the boothole bug*.

2. The Linux distro (in this case KDE Neon) must also have a shim that is aware of the boothole fix for the whole system to boot with secure boot in computers with the boothole fix.

3. But there are **problems** to create a persistent live drive, **when mkusb-dus is running in an installed system in UEFI mode**. I am working on that problem (additional fixes needed in mkusb for the boothole bug).

It is possible to create a system that works in UEFI mode and secure boot

- when running mkusb 12.6.0 in an installed system in BIOS mode, and
- when running mkusb 12.6.0 in a live or persistent live system both in BIOS mode and UEFI mode.

---

