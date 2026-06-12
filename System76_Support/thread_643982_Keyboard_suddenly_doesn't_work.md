---
title: "Keyboard suddenly doesn't work"
date: 2007-12-18
forum: System76 Support
---

### Post by contrariwise on 2007-12-18
Hiya.  The keyboard on my Gazelle has very suddenly stopped working.  Everything was working as normal, but when I tried to log back in after some idle time, the keyboard had suddenly stopped working.  I have tried a hard reset, but the problem persists.  The touchpad is working fine.

I apologize to say that I am quite new to Linux and I am utterly clueless as to what is going on here.

I would very much appreciate some advice.


UPDATE: I tried connecting a usb keyboard and that works fine.  Does this mean the hardware is destroyed or something?  I can't understand why this would just happen out of nowhere.

---

### Post by elliotjreed on 2007-12-18
Boot into the safe mode, and type in:

dpkg-reconfigure xserver-xorg

... Maybe with a 'sudo' in front, if it doesn't come up with anything!

This will allow you to go through (ignoring most to keep everything else the same) until you come to keyboard, and enter your keyboard details - select a driver!


Edit: God - I just realised how stupid that was... you can't type that command without a keyboard! If you can borrow (or have) an external one, use that to enter it!

---

### Post by thomasaaron on 2007-12-18
If that doesn't work, call me at support. Perhaps your keyboard's ribbon cable disconnected from it's socket. It is something we can check over the phone.

---

### Post by contrariwise on 2007-12-18
And now I'm typing from my working laptop keyboard!

Thank you, elliotjreed.  The problem actually turned out to be that the keyboard ribbon came loose, but thank you anyway.

Thank you lots, thomasaaron!

The support at System76 truly sets the company above and beyond its competitors.  I must certainly recommend the company to my friends.

---

### Post by thomasaaron on 2007-12-18
No problem. Sorry I made it so confusing. (Job security :lolflag:)

---

