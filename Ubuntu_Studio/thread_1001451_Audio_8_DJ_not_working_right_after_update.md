---
title: "Audio 8 DJ not working right after update"
date: 2008-12-03
forum: Ubuntu Studio
---

### Post by sakuramboo on 2008-12-03
I have been trying for the past few months to get the Native Instruments Audio 8 DJ to work in any flavor of Linux. I have tried Hardy, Ubuntu Studio Hardy, Gutsy, Ibex, 64 Studio 2.0 and 2.1, JAD and non of them worked. They would all either lock the system up or mixxx would crash. I followed the information found here...

[http://www.native-instruments.com/forum/showthread.php?p=460323](http://www.native-instruments.com/forum/showthread.php?p=460323)

And got it sort of working with Ubuntu Studio Ibex, however, since there is no realtime kernel and the only way I got that to work was with jackd, it was not playable. So I downgraded to Ubuntu Studio Hardy, created the ~/.asoundrc file and it was sort of working. Then I updated the packages and now it doesn't work at all. I keep on getting error messages that the device doesn't exist, yet the driver does load when it's plugged in.

Is there something I can do or do I need to continue to wait for the ALSA devs to fix [my bug report]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4271")?

EDIT: I have been documenting my progress with this and got it working to a point. It turns out the issue is with portaudio. But, anyway, here is my working documentation on this device.

[http://www.sakuramboo.com/wiki/index.php?title=Audio_8_DJ](http://www.sakuramboo.com/wiki/index.php?title=Audio_8_DJ)

---

