---
title: "experimental all_snap images"
date: 2016-08-20
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-08-20
Could someone please give me a memory refresh of what this is?  Does it have to do with snappy personal image?

> 
[SIZE=2]Hi,
 
 we have a set of new experimental images available at:
 
     [http://people.canonical.com/~mvo/all-snaps/16/]("http://people.canonical.com/%7Emvo/all-snaps/16/")
 
 These images fix some bugs around the new upgrade code in grub/uboot. So
 if you experienced strange issues here those should be fixed now (and
 our automatic tests got fixed to check for those).
 
 Note that the "amd64" image got renamed to "pc" to make it more
 consistent with the gadget snap name (but happy to revert that if its
 considerd too generic).
 
 As always, please give the images a go and let us know about any
 issues. We hope to move the images to a more offical place soon but we
 want to have some more testing first to ensure the upgrade issues are
 all resolved.
 
 Cheers,
  Michael (on behalf of the snapd team)
[/SIZE][SIZE=2]


Regards..

 [/SIZE]

---

### Post by grahammechanical on 2016-08-20
It is Snappy Ubuntu Core.

Back in December I downloaded from that all-snaps directory amd64-all-snap.img.xz and used Disks Restore Image to put it on a USB memory stick. It is 
command line and after log in we see "Snappy Ubuntu Core. A transactionally updated Ubuntu."

I guess that amd64-all-snap.img.xz is now named all-snaps-pc.img.xz. But is it built on vivid code or xenial code? This is Pocket Desktop but it is built on vivid code and when I put it onto a USB stick all I got was "Insert boot media."

[http://cdimage.ubuntu.com/ubuntu-pd/vivid/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-pd/vivid/daily-preinstalled/current/)

This is where Ubuntu Personal came from. And I now see that a new image has been built as of 25 May 2016. I might try it out. Correction! The important tar.xz file is still dated 17 October 2015. version-121.tar.xz would be the image to restore to the USB stick but it is not a new image.

[https://system-image.ubuntu.com/ubuntu-personal/rolling/edge/generic_amd64/](https://system-image.ubuntu.com/ubuntu-personal/rolling/edge/generic_amd64/)

Regards

---

### Post by ventrical on 2016-08-20
@graham

Thanks  very much!

Regards..

---

