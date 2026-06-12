---
title: "Issues with new panp7"
date: 2010-05-05
forum: System76 Support
---

### Post by magnumjones on 2010-05-05
Hey guys, I looked and didn't see anybody else having these things, but here are a couple of things I noticed and would like some help with:

I just upgraded to 10.04, but several of these problems were there before

1) the fingerprint reader is still broken - I know there is a fix for it in the works - still looking for a timetable.  
2) suspend has gotten stuck and needed to be rebooted.  2 out of 10-11 times suspending.  No change since 10.04 upgrade
3)hibernate seems broken.  I return from it and the display is segmented into a series of pulsating lines each about a centimeter thick and spaced about 5 cm apart.  A reboot is required. 2 out of 3 times trying to hibernate. no change since 10.04 upgrade
4)Since the upgrade to 10.04 - HDMI sound is gone.  I looked and someone else said a fix in the alsamixer helped, but my alsamixer shows no controls on the HDMI section.  Picture is great and so is the analog sound.  HDMI sound was working pre-10.04.
5) sometimes when I am using the touchpad the cursor starts flying all over the screen.  I have to let it go find where it went then guide it back after a slight(1 sec) pause.  If I don't wait the jumoing continues.  This is starting to grate on the nerves a bit

I upgraded today via the torrent-based alternate cd method.  I then upgraded system76 drivers after an upgrade to the system.

Any thoughts would be appreciated.

-Dan

---

### Post by thomasaaron on 2010-05-06
> 1) the fingerprint reader is still broken - I know there is a fix for it in the works - still looking for a timetable.

I've had another tech working on it, but so far we haven't been able to figure it out. So, it's difficult to provide a timetable. We're still working on it, though.

> 2) suspend has gotten stuck and needed to be rebooted. 2 out of 10-11 times suspending. No change since 10.04 upgrade

Suspend has gotten much better in Ubuntu, but most of the suspend/resume problems we see are with multiple consecutive suspend cycles. Please provide logs via the System76 Driver after the next occurrence, and we can have a look. Please start another thread when you're ready to do so, and please include times (when you tried to suspend, and when the computer came back up) so we can isolate the problem in the logs.

> 3)hibernate seems broken. I return from it and the display is segmented into a series of pulsating lines each about a centimeter thick and spaced about 5 cm apart. A reboot is required. 2 out of 3 times trying to hibernate. no change since 10.04 upgrade

TA: Same steps as above.

> 4)Since the upgrade to 10.04 - HDMI sound is gone. I looked and someone else said a fix in the alsamixer helped, but my alsamixer shows no controls on the HDMI section. Picture is great and so is the analog sound. HDMI sound was working pre-10.04.

TA: Most likely, it is a setting in your sound preferences. Did you look under the Output tab, at the connector drop-down?

> 5) sometimes when I am using the touchpad the cursor starts flying all over the screen. I have to let it go find where it went then guide it back after a slight(1 sec) pause. If I don't wait the jumoing continues. This is starting to grate on the nerves a bit

TA: I've seen some other folks report this, not juts on our machines, but across the board. It appears to be a buffer problem of some kind. There is a related bug report on it here...
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/365943](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/365943)

Make sure you've run all Lucid updates and rebooted. That might fix it. If not, enable backports and proposed in your Software Sources, under your Updates tab. Then run updates again and reboot. Did that fix it?

---

### Post by magnumjones on 2010-05-06
1) good stuff
2 & 3) So after the next occurrence "System76 driver"->Support->Create, then post the results?
4) I wish it were so simple.  I actually had that issue the first time I tried it.  I do have the output set to the HDMI output, and under the alsamixer it isn't muted.  
I don't know if this helps, but when I enter "aplay -l"

before plugging in HDMI cable:
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

after plugging in HDMI cable and playing some sound
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

5) on it and will tell you the results as I know them


Thank you for the quick response and all the help.  I gotta say I love the laptop otherwise.

---

### Post by isantop on 2010-05-07
I believe that the HDMI problem is actually a problem from the open-source graphics driver. Because the HDMI port is on the graphics card, the graphics drivers control sound output on it. Make sure you have the latest Proprietary ATI Driver installed (System > Administration > Hardware Drivers) and check again.

Please note the as of Ubuntu 10.04, the System76 Driver does not install the proprietary ATI drivers for the Panp7.

---

### Post by magnumjones on 2010-05-10
Any reason the proprietary drivers aren't getting used in 10.04?  Is there any danger of busting the system.  I only ask, because I rarely use HDMI, but I use the beast constantly for work, and can't risk the downtime.

Also, I started a thread for the Locking up Issue.

Thanks for all the help!

-Dan

---

### Post by thomasaaron on 2010-05-10
You're safe using the proprietary drivers.

---

