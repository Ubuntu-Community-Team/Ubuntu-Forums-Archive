---
title: "how to install chromium os to hdd?"
date: 2009-12-04
forum: The Cafe
---

### Post by QQi on 2009-12-04
i need install chromium os from usb/.image to hdd but dont want to run /usr/sbin/chromos-install

i try dd from image to /dev/sda4

#copy rootfs to /dev/sda4
sudo dd if=rootfs.image of=/dev/sda4
#copy mbr.image to master boot record of /dev/sda4 (primary + boot)
sudo dd if=mbr.image of=/dev/sda4 bs=446 count=1

and change boot in file /boot/extlinux.conf some thing like this

> DEFAULT [COLOR="Red"]chromeos-hd[/COLOR]
PROMPT 0
TIMEOUT 0

label chromeos-usb
  menu label chromeos-usb
  kernel vmlinuz
  append quiet console=tty2 initrd=initrd.img init=/sbin/init boot=local rootwait root=LABEL=C-ROOT ro noresume noswap i915.modeset=1 loglevel=1

label chromeos-hd
  menu label chromeos-hd
  kernel vmlinuz
  append quiet console=tty2 init=/sbin/init boot=local rootwait root=[COLOR="red"]/dev/sda4[/COLOR] ro noresume noswap i915.modeset=1 loglevel=1

Change the Lable of /dev/sda8 to "[COLOR="DarkRed"]H-STATE[/COLOR]" (extended)

when i try to boot it can't ;( 

"[COLOR="Red"]***Multiple active partitions.***[/COLOR]" 

what i do wrong ?

---

