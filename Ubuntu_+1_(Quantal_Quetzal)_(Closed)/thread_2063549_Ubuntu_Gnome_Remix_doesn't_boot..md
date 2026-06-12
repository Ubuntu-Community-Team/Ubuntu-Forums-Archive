---
title: "Ubuntu Gnome Remix doesn't boot."
date: 2012-09-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by DisappearingOak on 2012-09-27
Hi, UBuntu Gnome Remix Alpha 2 works in VirtualBox but I made a live USB with UNetBootin on an ext3 formatted 8GB pen but it doesn't boot. I get the bootloader menu entries (Try Ubuntu gnome Remix without installing, etc) but with any of the options it gives an error when booting: (initramfs) failed to mount /dev/loop0 on //filesystem.squashfs : no such device. I have tried reformatting and writing it to the pen drive again but same thing.

What should I do?

---

### Post by dino99 on 2012-09-27
Note that the USB drive must be formatted as FAT32

[http://sourceforge.net/apps/trac/unetbootin/wiki/guide](http://sourceforge.net/apps/trac/unetbootin/wiki/guide)

---

### Post by DisappearingOak on 2012-09-27
> **dino99 said:**
> Note that the USB drive must be formatted as FAT32

[http://sourceforge.net/apps/trac/unetbootin/wiki/guide](http://sourceforge.net/apps/trac/unetbootin/wiki/guide)

I tried with FAT32 and UnetBootin but just get "Boot error". Then I tried several times with FAT32 and dd command. But it doesn't boot and just goes over to hard disk's bootloader. Very weird. Maybe it's a Unetbootin version incompatibility. Can you tell me wyhat version of Unetbootin I require for the gnome remix alpha 2 iso?

---

### Post by dino99 on 2012-09-27
Also with some usb sticks, their formated table is borked, so with gparted or similar tool, before formatting as FAT32, the table need to be rebuilt first (from the gparted menu option)

---

### Post by DisappearingOak on 2012-09-27
> **dino99 said:**
> Also with some usb sticks, their formated table is borked, so with gparted or similar tool, before formatting as FAT32, the table need to be rebuilt first (from the gparted menu option)

I know. Actually this was an incompatibility with unetbootin, as I found a newer version on the sourceforge website and that worked perfect. thanks

---

### Post by Stinger on 2012-09-27
> **DisappearingOak said:**
> I know. Actually this was an incompatibility with unetbootin, as I found a newer version on the sourceforge website and that worked perfect. thanks
Good you got it working :)
Can you mark this thread as solved please ?

---

