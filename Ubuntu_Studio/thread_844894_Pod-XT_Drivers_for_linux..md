---
title: "Pod-XT Drivers for linux."
date: 2008-06-30
forum: Ubuntu Studio
---

### Post by d3drocks on 2008-06-30
so, i have a Pod-XT.
being a registered user at Line6.com, i asked if there were any drivers. i got my answer: [http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/)
so, i followed the instructions. it compiled, and seemed to place itself in the right folders, but when i turned on my pod, Ubuntu didn't do anything. not even acknowledge that it was plugged in.

can i have some help please?

btw, im using 8.04 hardy heron, in Gnome.

---

### Post by BoxOfSnoo on 2008-07-23
I haven't set it up on my Ubuntu box yet, but did you load the module?  Do that and check dmesg to see if it's recognized.

---

### Post by Bibiwinter on 2008-07-24
Hi,

  Also tried to install the PodXT driver on Hardy but didn't even get as far as you.  Here is the results of my "make install":

root@Tweety:/home/seb/Desktop/Driver PodXT/line6usb-0.7.3# sudo make install
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/seb/Desktop/Driver PodXT/line6usb-0.7.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `PodXT/line6usb-0.7.3'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
root@Tweety:/home/seb/Desktop/Driver PodXT/line6usb-0.7.3#

root@Tweety:/home/seb/Desktop/Driver PodXT# uname -a
Linux Tweety 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

As I'm a newbie to linux and have no programming background, I have no clue where to start.   Any hint??

Thanks!

---

### Post by d3drocks on 2008-07-30
> **BoxOfSnoo said:**
> I haven't set it up on my Ubuntu box yet, but did you load the module?  Do that and check dmesg to see if it's recognized.

im a complete noob. srry, how do i do that?

---

