---
title: "Using a second cd/dvd drive (usb)"
date: 2010-07-23
forum: System76 Support
---

### Post by ajlewis2 on 2010-07-23
I have Daru1 with Lucid Lynx installed.  My internal dvd sometimes does not work well.  I have an external usb cd/dvd drive that I bought for my netbook and which works on it in both Windows and Ubuntu.

I have tried to access the external usb drive on my laptop.  It spins and the light comes on, but I have not been able to use it.  I'm guessing that it should try to mount on sr1 where sr0 is used for the internal drive.  

Any ideas how I could get it to work on the laptop?  I have the info I would need to write a udev rule, but I don't know what rule I could use as a basis for writing it.  I do not know how to write one from scratch.

Thanks.

---

### Post by msrinath80 on 2010-07-23
I've seen that some of these external CD/DVD drives spin up but never work unless both USB cable ends are plugged in. Does your drive have two ends that have a female USB plug?

---

### Post by ajlewis2 on 2010-07-23
Thank you.

My drive has only one plug which I think is called the Standard B.  There is just one cable that plugs into that and then the other one has the plug that goes into the computer.

The drive does work fine in my netbook which does not have an internal cd/dvd drive.

---

### Post by ajlewis2 on 2010-07-26
Ok, I think I fixed this problem by frying the usb ports; so it is no longer an issue.  DVD, mouse, and ports seem to be fried from applying too much outside power to the DVD drive while plugged into the port.  Dumb.  Very dumb!

---

