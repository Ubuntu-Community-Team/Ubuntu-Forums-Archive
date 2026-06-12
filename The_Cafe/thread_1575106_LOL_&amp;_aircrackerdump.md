---
title: "LOL &amp; aircrackerdump"
date: 2010-09-15
forum: The Cafe
---

### Post by johnuk on 2010-09-15
I love the direct nature of the air suite;

john@john-desktop:~$ sudo airodump-ng ath0
Interface ath0: 
ioctl(SIOCGIFINDEX) failed: No such device
john@john-desktop:~$ airmon-ng start wlan1
**Run it as root** *{edit: nooooob}*

Some of you may have been trying to run this using the guides and keep getting the device errors with things like ath0 in there. I did a right click on my connection bar, then went to connection information and found it was calling the WiFi adaptor wlan1.

That might help a few of you.

---

### Post by Cuddles McKitten on 2010-09-15
You'd love sudo compiled with the insults option enabled, then.  OpenBSD comes with that in their default install.

---

