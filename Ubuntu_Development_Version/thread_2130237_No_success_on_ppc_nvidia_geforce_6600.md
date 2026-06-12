---
title: "No success on ppc nvidia geforce 6600"
date: 2013-03-28
forum: Ubuntu Development Version
---

### Post by gusduenas on 2013-03-28
Hello I've been trying with no success to install raring on mac ppc dual 2.0GHZ with geforce 6600 :

1. For starters, the screen went black and it says that my input devices and screen and device are not recognized.

2. It tells me to go with low graphics and it just stalls the machine.

3. crtl+alt f2 and I start Xorg -configure with the error that the number of detected screen doesn't match with the number of created screens.

4. I go with the cp /root/xorg.con.new /etc/X11/xorg.conf

5. sudo start lightdm and finally I got the screen in color, but only the screen and the mouse pointer, not menu at all and there is an error to report about Xorg.

So how can I install this raring ringtail onto my mac g5 ppc (the live cd says is for that).

This is my story, so I hope someone can help me out.


Thanks.


Gus

---

### Post by gusduenas on 2013-03-29
still on this, at this time no success I think that even the 12.04 is not good for ppc g5 with nvidia

---

### Post by dino99 on 2013-03-29
you should not use xorg.conf as it conflict with the actual default kernel settings

sudo rm /etc/X11/xorg.conf

is it better with "nouveau" driver ?

---

### Post by gusduenas on 2013-03-29
Thanks Dino, well I've been using the desktop DVD and I cannot see a thing on the desktop since ubuntu keep tells me that my card (device) and monitor and input has not been properly detected, then since I try to use the low graphics mode and nothing happens, still black script and modal window...nothing else, then I try to use the xorg.conf with sudo lightdm start and I finish on the background in color and the pointer.
My card is a Nvidia Geforce 6600 256mb mac with two dvi port, on one is a cinema display 23" and the machine is a dual g5 2.0ghz Power PC...so any hint to install it will be appreciated. BTW also it tells me that the monitor is not detected...why is that? I tried switching the monitor from the other place but Ubuntu didn't read it then.

Gus

---

### Post by gusduenas on 2013-04-05
well no one with ideas, is discouraging for ppc users to migrate to ubuntu since looks like there is no people with answers...

---

