---
title: "Is it possible to create a minimal ubuntu installed iso."
date: 2018-07-03
forum: Ubuntu, Linux and OS Chat
---

### Post by djking101 on 2018-07-03
I was thinking that many people use puppy Linux because it can run in a single iso file and they wont have to install it, so I was thinking could we create an iso that is as stock as possible - but can still store apps and data in an sfs? I know Puppy is based on Ubuntu but has a different desktop(JWM) and doesn't use apt, snaps, etc. ;)

_**PLEASE DONT MENTION WOOF CE - IT DOES NOT WORK (I TRIED) :frown:**_

---

### Post by djking101 on 2018-07-06
Hi. I can install to a usb - could we create an iso from that?

---

### Post by sudodus on 2018-07-06
You can create a **persistent live** USB drive with Ubuntu or an Ubuntu community flavour (Kubuntu, Lubuntu, ... Xubuntu) with a partition labeled **casper-rw** for persistence. The partition labeled **casper-rw** can be in the USB drive, but also in an internal drive.

If you want control of what is happening, you should only have one partition labeled **casper-rw** connected.

(It is also possible to have a file named **casper-rw** in a partition with a FAT32 file system, but it will be limited to 4 GB.)

See the following links,

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

[hr][/hr]
It can also be a good idea to ***install* Ubuntu or an Ubuntu community flavour into a USB drive** (a fast USB 3 pendrive or even better a USB connected SSD) like installed into an internal drive. See the following link,

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

Such a drive is portable between computers, but not as portable as a [persistent] live drive.

---

### Post by C.S.Cameron on 2018-07-06
A Ubuntu minimal install is about **3.5GB** and has a few apps, a Puppy install is under **300MB** and has lots of apps.

---

