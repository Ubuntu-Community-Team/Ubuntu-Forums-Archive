---
title: "Xorg 1.15 : is it gonna make it for trusty release?"
date: 2014-01-06
forum: Ubuntu Development Version
---

### Post by spupazza on 2014-01-06
Version 1.15 was released on 27th December.
I was wondering if (and when, if anybody knows) it'll make it in trusty release

[http://www.phoronix.com/scan.php?page=news_item&px=MTU1NDQ](http://www.phoronix.com/scan.php?page=news_item&px=MTU1NDQ)

---

### Post by grahammechanical on 2014-01-07
Keep watching the kernel team blog.

[http://voices.canonical.com/kernelteam/2014/01/](http://voices.canonical.com/kernelteam/2014/01/)

As of today's update to my Trusty installation the version being used is 1.14. Ubuntu 14.04 will still be using the Xserver. So, we can expect upgrades of the Xserver to be brought into Trusty Tahr but as noted in that blog the Ubuntu developers will have to add their own patches for Mir and perhaps also for Wayland and who knows how long that will take.

> [COLOR=#000000][FONT=verdana]For now the Wayland and Mir developers are carrying their own out-of-tree patches against the xorg-server code-base. [/FONT][/COLOR]

Regards.

---

### Post by spupazza on 2014-01-07
Thanks a lot for the link and the explanation about why the new version isn't there yet.

---

### Post by pferraro on 2014-01-08
Probably.  xorg-server 1.15 was uploaded to the ppa:canonical-x/x-staging ppa yesterday.  This is usually a good indication that it will make its way to the main repos soon.

---

