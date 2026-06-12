---
title: "Trouble installing UNR on ASUS eee"
date: 2010-03-11
forum: Ubuntu Moblin Remix
---

### Post by HiRez_L on 2010-03-11
I just got an ASUS eee netbook, trying to install Ubuntu 9.10 UNR off a CD, I have a USB cd reader on the ASUS it boots fine off the CD, but after choosing install, drops me to a busybox prompt with the following error:
(intramfs) /init: line 1 can't open udevadm timeout of 180 seconds reached <snip> /block/sdb/sdb1 (1092) /dev/loop0: no such file
Mount: mounting udevadm settle - timeout of 180 seconds reached <snip> /block/sdb/sdb1 (1092) /dev/loop0 on //filesystem.squashfs failed: no such device
Can not mount udevadm settle -  timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/host3/target3:0:0/3:0:0:0/block/sdb/sdb1 (1092) /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

i have installed Ubuntu to a wide variety of desktops and laptops, and work as a Solaris admin, so I am fairly technical, but this is my first eee . . . not sure how to proceed.  Any help will be appreciated.

---

### Post by HiRez_L on 2010-03-11
Well, lacking responses, I tried installing Moblin and regular Ubuntu 9.10 too, got the same errors.  Then I tried booting with any Linux that people had reported working with the 4Gsurf (701), I got Puppeee 4.3.1 working, but I'd still rather have Ubuntu.

---

### Post by Alxl on 2010-03-12
HiRez_L,

maybe this will be of some help:  [http://ubuntuforums.org/showthread.php?t=1370066](http://ubuntuforums.org/showthread.php?t=1370066) 

I had trouble installing UNR on my eee  but after several attempts it finally worked and I am very happy with it .
I used a USB and the one I made from the Desktop  USB Startup Disk Creator did not work . But the USB that I made from a live CD did work.

---

### Post by Fenris_rising on 2010-03-12
Not sure why your having issues but I installed 9.10 onto a 904HD via usb stick. I used unetbootin to make the stick and it is great!

good luck

Regards

Fenris

---

### Post by HiRez_L on 2010-03-13
Well, I finally gave up on installing via CD and made a USB stick, and it installed perfectly.

---

