---
title: "Rhythmbox seek bug ?"
date: 2012-12-19
forum: Ubuntu Development Version
---

### Post by anca-emanuel on 2012-12-19
Play an song in rhythmbox.
Seek to forward, or something else.

I get an unresponsive program. Bug ?

p.s. VLC is working ok.

---

### Post by grahammechanical on 2012-12-19
I get the same here. 

Press Next once = works. Press Next twice or too quickly = window goes grey and Force Quit required.

Select a track, press Pause and then press Play = windows goes grey and Force Quit required.

This program does not like being made to Force Quit repeatedly. It now will not play at all. Or change albums. I may have to reboot to get it to start working again.

Update: Just give a few minutes to get its breath back but once an album is playing do not change anything.

I have been running top and rhythmbox disappears when it becomes unresponsive.

Update 2: changing the sound level on the Rhythmbox slider also puts it into Unresponsive mode. Edit: It the slider that moves forward through the track.

I am going to try a reboot. done that. Now playing again but I am not messing with it. Listening to Eddie Cochran.

Added comment to bug report.

Regards.

---

### Post by anca-emanuel on 2012-12-19
How do we report this ?

Edit: bug at [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1092246](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1092246)

---

### Post by ventrical on 2012-12-19
Working good here .. finally-! I always had problems with Rbox so I used Audacious. I was trying to emulate your bug .. but now it is working great.

---

### Post by mc4man on 2012-12-20
After removing the gstreamer1.0 pulseaudio plugin all gst players such as totem, Rb & banshee behave much better here.
(noted [http://ubuntuforums.org/showthread.php?t=2090486](http://ubuntuforums.org/showthread.php?t=2090486)
The exception would be 'slide' seeking (vs. 'click' seeking), which continues to cause an unresponsive player(s)


> **anca-emanuel said:**
> How do we report this ?

Edit: bug at [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1092246](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1092246)
You should put a proper bug description in your report, not a link to a forum thread.

---

