---
title: "Mouse wheel does not work using qemu-system-x86_64 ubuntu 13.10"
date: 2014-01-27
forum: Virtualisation
---

### Post by nodroglinux on 2014-01-27
I have tried many options to get this working but still with no avail.

I am running:

`qemu-system-x86_64 -smp 3 -m 3072 -cdrom /dev/cdrom -usb -usbdevice tablet ${HOME}/KVM/Images/Windows7-1.img -name win7 -M pc -enable-kvm -monitor tcp::2323,server,nowait `

I have a working mouse in my windows 7 VM but no scroll wheel at al,this used to work in previous versions of qemu and ubuntu.

I am running 

`qemu-system-x86_64 -versionQEMU emulator version 1.5.0 (Debian 1.5.0+dfsg-3ubuntu5.2), Copyright (c) 2003-2008 Fabrice Bellard`

My colleague is running QEMU 1.4.0 and his works fine.

What am I missing ??

I also noticed that the CTRL key has stopped working as well.

---

