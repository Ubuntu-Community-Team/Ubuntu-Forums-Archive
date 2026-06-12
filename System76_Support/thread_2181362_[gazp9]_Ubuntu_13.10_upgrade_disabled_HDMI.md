---
title: "[gazp9] Ubuntu 13.10 upgrade disabled HDMI"
date: 2013-10-17
forum: System76 Support
---

### Post by rlm1023 on 2013-10-17
I had been running Ubuntu 13.04, with GNOME 3 instead of Unity, for some time with no issues. I had a triple monitor setup (laptop screen @ 1920x1080, VGA at 1920x1200 and HDMI at 2560x1440). I'd had to manually set up xrandr to push HDMI through at that resolution, but it was working with no (or at least few) problems.

I just upgraded to Ubuntu 13.10, and I'm noticing that xrandr isn't even reporting the HDMI out anymore (and naturally the computer can't detect displays connected to it). Here is my xrandr output:

rob@stealth:~/Downloads$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1920x1080      60.0*+   59.9  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

Any ideas?

---

### Post by houstonbofh on 2013-10-17
Did you re-enable the third party repositories and update the system76 driver package?

---

### Post by rlm1023 on 2013-10-18
Augh! That seems to have fixed it. I had reinstalled the system76 driver, but there was a gnome repository that got unchecked. It appeared after enabling that... strange.

Thank you!

---

### Post by houstonbofh on 2013-10-18
Every upgrade disables all the 3rd party repos.

---

