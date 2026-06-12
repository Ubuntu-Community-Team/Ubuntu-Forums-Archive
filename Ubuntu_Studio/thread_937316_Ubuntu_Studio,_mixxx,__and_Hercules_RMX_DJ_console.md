---
title: "Ubuntu Studio, mixxx,  and Hercules RMX DJ console"
date: 2008-10-03
forum: Ubuntu Studio
---

### Post by 2_of_8 on 2008-10-03
I have a HP Pavilion dv6418ca ([detailed specs on official HP site]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01062882&lc=en&dlc=en&cc=us&lang=en&product=3444083#")). I like the idea of having a distro tailored towards audio/video/design, so I decided to try this. I installed Ubuntu Studio with no problems. 

I would like to use my Hercules RMX DJ controller with some DJ application - probably Mixxx, as it seems to be free and the most supported one out there. But I have no preference. In Windows, I've used VirtualDJ and Traktor.

I've tried to look online for instructions on how to do this, and have not gotten very far. I've fiddled with "Jack Setup", but I am quite clueless. I would love to get some guidance with this process, and would be very grateful to whoever can help me get this working.

---

### Post by Stochastic on 2008-10-04
If I recall correctly, last time I looked into the RMX support for mixxx, it was revealed that this new device is supported in the newest version of mixxx (or was that the hardware driver within mixxx), but the current Hardy repo version falls behind.  Ahh here's that original thread: [http://ubuntuforums.org/showthread.php?t=880012&highlight=RMX](http://ubuntuforums.org/showthread.php?t=880012&highlight=RMX)

---

### Post by 2_of_8 on 2008-10-05
Alright, after a bit of struggle with un-tarballing and installing and dependencies, Mixxx 1.61 is posted. The options to pick Hercules RMX are there under "Sound hardware", "Input controllers" and "Vinyl control". I've picked them where possible, but I don't know what to do next.

---

### Post by 2_of_8 on 2008-10-09
Bump please =)

---

### Post by Stochastic on 2008-10-09
I can't help much more than I already have, but the thread I linked to above, does give these words of advice: > It's solved now, the howto is on the mixxx.org forums...
It's just a matter of adjusting a xml-file, and installing an up to date "libdjconsole"

If you're still stuck after that, I'd try posting in the mixxx forums, it's quite active in there.  (and then of course post back here any results so that others can see how you solved the problem)

Edit: ahh, here's the thread that joecheem67 was talking about (I think): [http://mixxx.org/forums/viewtopic.php?f=3&t=183](http://mixxx.org/forums/viewtopic.php?f=3&t=183)

---

