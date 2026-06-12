---
title: "How to change sound device in xfce?"
date: 2012-03-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jp021980 on 2012-03-15
I just installed Ubuntu 12.04 and then installed xfce.  Sound works fine through my normal sound card, but I can't get it to work with my USB headphones.  The headphones are detected (they've always worked with with Ubuntu) but sound seems to be directed to speakers going through the soundcard.  How can I have sound directed to the headset?

---

### Post by screaminj3sus on 2012-03-15
XFCE's is mixer doesn't seem to have a way to set the output device, it lets you select the device and change its volume, but not actually set its output :/. thats always bothered me about XFCE.

Best bet is to install pavucontrol and use that to set the output device (you can also install the gnome sound applet, but I believe that pulls in the whole gnome control center now)

---

### Post by jp021980 on 2012-03-16
That did it (pavucontrol).  Thanks a lot for the help!

---

