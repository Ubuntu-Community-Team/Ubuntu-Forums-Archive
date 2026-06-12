---
title: "Need help setting up useful portable Linux"
date: 2008-05-10
forum: Virtualisation
---

### Post by buu700 on 2008-05-10
Hi. I've researched and tried a lot of things, but nothing seems to work. I have a 4GB USB flash drive, and I'm trying to set it up so that I have Debian or any Debian-based distro (with GNOME (or maybe Xfce), if it matters) bootable and persistent from my flash drive, as well as accessible and persistent from QEMU in Windows (preferably with QEMU on the same drive, but could be on a different drive if necessary), with at least 300MB of space left on the drive, readable in Windows, QEMU, and from booting the USB drive straight through the BIOS. If this is possible, then what's the best/closest I could do (and how)? Thanks.


EDIT: I think andLinux would be perfect for me (I could just carry around a separate liveCD just in case though I guess if I need it), but does anyone know if it will run off of a flash drive?

---

### Post by dcstar on 2008-05-10
> **buu700 said:**
> Hi. I've researched and tried a lot of things, but nothing seems to work. I have a 4GB USB flash drive, and I'm trying to set it up so that I have Debian or any Debian-based distro (with GNOME (or maybe Xfce), if it matters) bootable and persistent from my flash drive, as well as accessible and persistent from QEMU in Windows (preferably with QEMU on the same drive, but could be on a different drive if necessary), with at least 300MB of space left on the drive, readable in Windows, QEMU, and from booting the USB drive straight through the BIOS. If this is possible, then what's the best/closest I could do (and how)? Thanks.


EDIT: I think andLinux would be perfect for me (I could just carry around a separate liveCD just in case though I guess if I need it), but does anyone know if it will run off of a flash drive?

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by buu700 on 2008-05-11
Thanks, but that wasn't exactly what I was looking for (and it's not compatible with Hardy, but Pendrivelinux has a great guide for Hardy here: [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)). What I was looking for was basically a way to have a single Linux installation accessible by booting off the USB or going into a portable VM, while sharing files with a partition readable by Windows (basically, a persistent installation of a Debian-based distro that used an NTFS partition as the ~/Desktop folder, with the NTFS partition having a QEMU setup that could boot from the same flash drive). Sadly, I couldn't figure out exactly how to set this up, but I think andLinux (Xfce variant, 2.5GB) would be the best solution for me.

EDIT: andLinux isn't portable, so I guess I still need help with this.

---

### Post by buu700 on 2008-05-11
Actually, I think I got it, if anyone else wants to see my (currently theoretical) setup:

> I'll setup a persistent Ubuntu installation using these instructions, for the most part: [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

Part of what I'll change is having a large partition at the top readable by Windows (either by just making that FAT partition larger or by creating a separate NTFS partition).

I'll have my Windows-compatible partition hold all my files and act as the ~/Desktop folder in Ubuntu.

On the Windows-compatible partition, I'll also use this to set up a Pendrivelinux persistent QEMU setup: [http://www.pendrivelinux.com/2007/09/19/portable-qemu-persistent-pendrivelinux/](http://www.pendrivelinux.com/2007/09/19/portable-qemu-persistent-pendrivelinux/)

I'll change the line of the "LaunchPDL.bat" file that actually starts QEMU from *.\qemu\qemu -L .\qemu -kernel-kqemu -std-vga -localtime -soundhw all -m 512 -cdrom *.iso -hda casper-rw.img -boot d* to *.\qemu\qemu -L .\qemu -kernel-kqemu -std-vga -localtime -soundhw all -m 512 -cdrom *.iso -hda casper-rw.img -hdb \\.\PhysicalDrive***X*** -boot d*, with **X** being the number of my flash drive (I'll find out later what that number will actually be).

In Pendrivelinux, I'll have my Windows-compatible partition hold all my files and act as the ~/Desktop folder.

Theoretically, that's all I need to do to get my ultimate portable Linux setup! I'll post back with the results (and if it works create a new thread with my instructions as a guide). Oh, and by the way, including shipping, my 4GB flash drive (new, cool looking, black) was only $14.99, which is pretty cheap relative to just a few years ago, especially considering the current state of the US dollar.

---

