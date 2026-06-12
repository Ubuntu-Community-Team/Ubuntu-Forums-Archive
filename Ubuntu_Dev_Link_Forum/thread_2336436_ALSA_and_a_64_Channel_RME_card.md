---
title: "ALSA and a 64 Channel RME card"
date: 2016-09-08
forum: Ubuntu Dev Link Forum
---

### Post by thingfish47 on 2016-09-08
Hi Guys,

Background - I am trying to port an audio app from Windows to Linux.  ALSA seems to be the best way to go as the async callback seems similar to the asio drivers from Steinberg for windows that I am used to using.

The alsa.org website has sample code that I have got working, but it only uses 2 of the 64 channels.  The -v option shows that alsa is aware of the other 62, but I am failing miserably getting the sinewave to appear on channels other that 1 and 2.  I suspect this is a configuration issue for .asoundrc but any advice would be greatly appreciated.

---

