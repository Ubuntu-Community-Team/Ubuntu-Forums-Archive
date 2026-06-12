---
title: "qemu usb stick"
date: 2008-09-26
forum: Virtualisation
---

### Post by threegremlins on 2008-09-26
I need to update the image for a friends book cover and to avoid headaches i would like to use windows program.  I installed virtualbox and after a reboot there was no entry to my nvidia card, already this is becoming a headache because I didn't want to mess around configuring my video and wacom. Away it went. I've used Qemu before but I can't get Qemulator to mount the usb stick and I'm not efficient with the command line.

I forgot to add that I used these command lines
 qemu -hda xp.img -m 756 -usbdevice /dev/sdb -localtime
and
 qemu -hda xp.img -m 756 -usbdevice /dev/sdb1 -localtime

according to mtab /dev/sdb1 is my usb stick

---

### Post by threegremlins on 2008-09-30
problem taken care of, switched to mint again, virtualbox works fine

---

