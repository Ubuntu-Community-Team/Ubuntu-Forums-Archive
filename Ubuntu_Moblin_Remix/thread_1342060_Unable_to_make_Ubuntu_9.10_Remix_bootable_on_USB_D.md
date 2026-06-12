---
title: "Unable to make Ubuntu 9.10 Remix bootable on USB Drive"
date: 2009-11-30
forum: Ubuntu Moblin Remix
---

### Post by lightningbuzz on 2009-11-30
Hello,

I have a problem with booting and installing Ubuntu Remix from USB drive.

With the same key, I managed to install Ubuntu 9.04 Remix and Moblin 2.1 without problem, but Ubuntu 9.10 Remix will not boot. The USB Bootable drive is never detected and I mean on the same computer (netbook MSI Wind) with the same config boot.

The only difference is the file type of the img: ISO for 9.10 and IMG for 9.04 and Moblin. But I have no error message and I tried both usb-creator and Unetbootin.
I think that the creation tools have a problem or misconfiguration and they create the wrong area for boot ... or the image has a problem.

If anyone has any leads ...

PS: I'm really disappointed especially after a 9.04 to 9.10 update that has completely screwed up my install

---

### Post by yannickroy on 2009-11-30
I had the same problem and my netbook - a samsung N310, requires that you insert the USB device before boot up, boot the computer,  go into BIOS setup and select the actual USB device in the boot order.

i.e. there was no generic option for booting from USB, you have to select the actual device in the boot priority list.

Worked fine once I figured this out.

---

