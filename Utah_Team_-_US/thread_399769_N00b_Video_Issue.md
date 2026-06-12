---
title: "N00b Video Issue?"
date: 2007-04-02
forum: Utah Team - US
---

### Post by Narfex on 2007-04-02
When ever I load up my computer the screen goes blank with a blinking cursor. after the blinking cursor goes away my monitor turns off stating that the screen resoloution is to high, I have tried this with 3 different monitors with the same result. Any Help?

---

### Post by stuporglue on 2007-04-02
To reconfigure your graphics, boot in recovery mode (At the grub loading screen, press escape, choose the recovery option -- probably 2nd from the top). 

In recovery mode, once you log in, type "dpkg-reconfigure xserver-xorg"

It will ask a bunch of questions, then dump you back on the command line. At the command line, type "reboot" and try your newly configured graphics setup.

---

