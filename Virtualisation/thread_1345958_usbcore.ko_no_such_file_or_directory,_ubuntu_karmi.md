---
title: "usbcore.ko no such file or directory, ubuntu karmic"
date: 2009-12-04
forum: Virtualisation
---

### Post by Major Squirrel on 2009-12-04
Hey guys,

I am trying to set windows xp in virtualbox so that I can use photoshop, illustrator and itunes for my iPod. I have tried and tried with no to get my ipod to work in ubuntu but it either doesn't get recognized (most music players) or it won't sync (rhythmbox) so I have given up and am going to use a vm of xp pro. I followed the instructions on this site [http://maketecheasier.com/sync-ipod-touch-with-win-xp-vm-in-ubuntu-intrepid/2008/12/16](http://maketecheasier.com/sync-ipod-touch-with-win-xp-vm-in-ubuntu-intrepid/2008/12/16) to set up usb support. Now I know I don't have intrepid or an ipod touch (i have a 6th gen classic 160gb) but I figured it was the same concept. Anyway, it all works fine until I get to

make -C /lib/modules/`uname -r`/build/ M=`pwd` modules 

It says install: cannot stat `usbcore.ko': No such file or directory

How do I get around this or where can I find it?

My linux kernal is 2.6.31 by the way

Thanks for the help

---

