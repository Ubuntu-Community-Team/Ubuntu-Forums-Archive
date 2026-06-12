---
title: "ubuntu 12.04 not booting"
date: 2011-12-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by shubham1 on 2011-12-11
i am trying to install ubuntu 12.04 i have downloaded the iso amd64 bit and used the startup disk creator
but when i boot in it says unknown key words :some keywords which are not there in keyboard
and 
no default ui configuration directive found

---

### Post by BC59 on 2011-12-11
Maybe is the USB creator which cannot create correctly the bootable .iso. I tried Unetbootin and it's working better. If no try to burn a CD.

Unetbootin you can download it from Ubuntu Software Center.

---

### Post by shubham1 on 2011-12-11
> **BC59 said:**
> Maybe is the USB creator which cannot create correctly the bootable .iso. I tried Unetbootin and it's working better. If no try to burn a CD.

Unetbootin you can download it from Ubuntu Software Center.
does not works

---

### Post by coffeecat on 2011-12-11
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by shubham1 on 2011-12-11
your software works fine i tested it with fedora

---

### Post by jppr on 2011-12-11
Yesterday I did fresh live-cd amd-64 [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/) installation and usb creator works fine
and system boot and works without any :popcorn:problems

---

### Post by shubham1 on 2011-12-11
ok

---

### Post by jerrylamos on 2011-12-11
I find it easier just to boot off the .iso I've copied onto a usb.  Sometimes usb creator is a bit messy to run for me, and in any case slower than a simple copy.

To do thiset up grub to boot of the usb once.  Then you can copy a .iso onto the usb and try it out or even do an install from it.  

See what your usb drive is, by doing a "df" in a terminal session.  Mine is /dev/sdc which to grub is hd2,1   if yours is /dev/hdb then grub would use hd1,1 in the code below.

In a terminal session edit a file and then copy the following into it:

```
gedit 40_custom

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "precise sdc1 USB" {
set isofile="/precise-desktop-i386.iso"
loopback loop (hd2,1)$isofile
linux (loop)/casper/vmlinuz boot=casper persistent iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

save

exit

sudo chmod 777 40_custom

sudo cp 40_custom /etc/grub.d

sudo update-grub
```

The 40_custom entry only has to be created once per install while you can try different .iso's out by just copying them to the usb.

Now re-boot, you can select the usb .iso and try it out.

Jerry

---

### Post by shubham1 on 2011-12-12
i am doing it and i will tell you what happened

---

### Post by shubham1 on 2011-12-12
when i booted then i typed the name of the iso file and then it obtted the file and then thre were some characters and things on the screen

---

### Post by shubham1 on 2011-12-12
are they virus

---

### Post by cariboo on 2011-12-12
The op's comments in this thread have so little content, it is hard to help. The final post, makes me think that this thread isn't serious. Thread closed.

---

