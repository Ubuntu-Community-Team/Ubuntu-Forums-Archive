---
title: "Upgraded to 9.10 - now my system doesn't work"
date: 2010-01-08
forum: System76 Support
---

### Post by mungo63 on 2010-01-08
I upgraded my System76 machine from Ubunutu 9.04 to 9.10.  There was apparently some problem with the nVidia graphics driver.  Now the Ubuntu gui will not come up.  I can login thru the command line.  Any help on what steps to take to recover would be greatly appreciated.

---

### Post by revlimiter on 2010-01-09
If it's a graphic driver issue, try blowing away your xorg.conf 

mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broke

Then it should boot with generic graphics drivers and you can try installing the good ones again.

---

### Post by thomasaaron on 2010-01-11
I would do the above.

THEN, I would go to System > Admin > Hardware Drivers and disable your nVidia driver. Then re-enable it. Then reboot.

---

