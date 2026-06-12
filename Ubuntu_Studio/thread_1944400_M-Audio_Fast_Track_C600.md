---
title: "M-Audio Fast Track C600"
date: 2012-03-21
forum: Ubuntu Studio
---

### Post by umea on 2012-03-21
I have a M-Audio Fast Track C600.
Does it work with Ubuntu studio?

---

### Post by jejeman on 2012-03-21
Try and see.
Download plane ubuntu the version you want to use and try it in Live mode.

---

### Post by umea on 2012-03-23
I can't make it work on linux!

---

### Post by sgx on 2012-03-26
look at older threads for fast track pro, and delta 1010 here, and on google, a lot of steps to configure and implement the card will be the same.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

links 4 and 8 at the wiki
will help set up the system, and show where to select the card,
if indeed it is recognized. If its a new hardware, not using
the older chipsets, it may not get alsa support.

aconnect -i
arecord -l
cat /proc/asound/cards

output from these should mention your recognized sound devices.
Cheers

---

