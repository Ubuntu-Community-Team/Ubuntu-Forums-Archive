---
title: "Dell Latitude D620 USB boot???"
date: 2013-05-09
forum: Ubuntu, Linux and OS Chat
---

### Post by mips on 2013-05-09
Trying to boot linux from a USB flash memory stick and not having any joy. The boot menu does not even show a USB stick as a boot option. BUT should I insert a bootable freedos stick into the port it's gets recognised and I can boot from it.


I've tried several different flavours of linux (*buntu, debian, arch) where I've written the image to the stick using dd and they work on other computers but when plugged into the dell the memory stick is not even recognised. A bootable freedos image will allow the mem stick to be shown in the bios and you can boot from it?


I've updated the bios to the latest A10 version, does not help. i've checked the usb settings (allow legacy etc) and change boot option and nothing seems to work.


I'm stumped, any ideas?

---

### Post by cariboo on 2013-05-09
What are you using to create the usb device? The only program I've had any problems with is unetbootin, the initial boot menu never shows, but it does boot.

I'd suugest you try the following command to create a bootable usb device:

```
sudo dd=if<iso_name> of=/dev/sdc bs=1M
```

---

### Post by lykwydchykyn on 2013-05-09
I've always had good luck with [multisystem](http://liveusb.info/dotclear), which uses grub2 on a FaT32-formatted USB stick to host multiple iso files.  I work with a lot of Dell hardware at work, and it's always worked with them.

If you're just using dd and an iso file, your stick is going to end up formatted iso9660; that may explain why the laptop has trouble with a stick like this, but not with a freedos boot image (which would use some kind of FAT format).

---

### Post by mips on 2013-05-10
I use dd.

Anyway I figured out if I insert the freedos stick and replace it at the boot menu with a linux one and hit enter it boots. So I can at least boot stuff off it which is cool.

---

