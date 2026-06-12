---
title: "Qemu Q35 machine HDD boot"
date: 2014-01-24
forum: Virtualisation
---

### Post by DZIANIS on 2014-01-24
Hello everyone. I have problems with launch qemu with machine type Q35 from HDD.
I use this command:
*qemu-system-i386 -m 2048 -cpu host -usb -vga cirrus -enable-kvm -soundhw ac97** -M pc-q35-1.7** -usbdevice mouse -hda /dev/sd*a
but I get "No bootable device":
[ATTACH=CONFIG]249711[/ATTACH]
I's because option:* '-M pc-q35-1.7'*. And it appears with all Q35 (Q35 + ICH9, 2009) machine types, independently of version (*'-M pc-q35-1.X'*), where X = [4; 7].
But all works with machine type i440FX (i440FX + PIIX, 1996). Option is from* '-M pc-0.10'* till* '-M pc-1.3'*.
So with command
*qemu-system-i386 -m 2048 -cpu host -usb -vga cirrus -enable-kvm -soundhw ac97 **-M pc-1.3** -usbdevice mouse -hda /dev/sda*
all launch sucussfull.
[I found similar question,]("http://lists.nongnu.org/archive/html/qemu-discuss/2013-08/msg00034.html") but not about boot from HDD, and this problem [resolved by using '-drive file=/../..' syntax]("http://lists.nongnu.org/archive/html/qemu-discuss/2013-01/msg00031.html") unlike my question.
So, how I can boot qemu with machine type Q35 from HDD?
Does anyone have any suggestions as to what I'm doing wrong or missing?

---

### Post by DZIANIS on 2014-01-26
Or maybe someone know, where else I can ask to resolve problem?

---

