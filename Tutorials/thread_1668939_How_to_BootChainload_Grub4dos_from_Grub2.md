---
title: "How to Boot/Chainload Grub4dos from Grub2"
date: 2011-01-17
forum: Tutorials
---

### Post by dbzkid on 2011-01-17
I am writing this finding because I did a lot of searching to find this and hopefully will help others. Also I didn't find a good solution for booting "Hiren's boot cd"(I hope I am allowed to write this) from USB through Grub2 for hours.

First of all you need to download a few things:
1) Grub.exe (Find the latest here... [http://download.gna.org/grub4dos/]("http://download.gna.org/grub4dos/") Download the zip file and inside is the grub.exe)

2) grldr (This is also in the zip file you downloaded)

3) menu.lst (Since I am trying to boot Hirens, I am using the one provided in the image. You can create your own, or use someone else's)

4) Have Grub2 installed on your distro (I did this on Ubuntu 10.10 x64)

What I did was install grub2 on to the MBR of the usb drive
```
grub-install --no-floppy --root-directory=/mnt/USB /dev/sdx (replacing  x with your actual USB device) and the "--root-directory=" should point to where your usb is mounted.
```
The above code should install Grub2 on to the usb drives MBR.

Next you can create your menu file (grub.cfg) using your favorite text editor. In the grub.cfg file you should make a menu entry thats looks like so... (This file is to be placed in "/boot/grub/" so it looks like so: /boot/grub/grub.cfg)

```
menuentry "Grub4dos"{
setroot=(hd0,1)
linux /grub.exe
}
```
At this time you should place your grub.exe and grldr on to the root of your usb.

This will allow you to boot the grub4dos boot loader.
Once you are This far you can then boot up Items that you normally boot from grub/grub4dos. At this time it would be great that you place your menu.lst on to the root of your usb.

You should be able to Boot into grub4dos from grub2 after this. Hopefully this will help! (Also Hopefully I am allowed to mention Hirens, can the moderators just edit it out, thanks.)

Sources:
[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Loading_GRUB_for_DOS_using_other_boot_loader]("http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Loading_GRUB_for_DOS_using_other_boot_loader")

[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/]("http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/")

---

### Post by amigos83 on 2012-02-03
Another way, for me easier, faster and works:)

You have to do almost everything like in this solution

[http://www.hirensbootcd.org/usb-booting/](http://www.hirensbootcd.org/usb-booting/)

Additional to this solution:
1. When you install grub check "Grub2"
2. Then rename the file "gldr" in root folder on USB Stick for "g2ldr"

I have Abit IP35-E and has problem with grub, BIOS freezes, with grub2 everything its ok.
I spend over 2 hours to find out whats the problem and to solve it in this way.

I hope that will be helpfull:)

---

