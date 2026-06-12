---
title: "Daru2 - multiple monitors (more than xrandr?)"
date: 2008-04-07
forum: System76 Support
---

### Post by imhavoc on 2008-04-07
I've been playing with xrandr on my Daru2. It's nice to be able to turn on and off an external monitor at will.

I've created a couple of buttons on my KDE bar to turn the external monitor on:
xrandr --output VGA --auto

and turn the external monitor off:
xrandr --output VGA --off

The limit I'm hitting right now is that I can only operate the two monitors as a single virtual desktop. Either they have 100% overlap (duplication), or I can only offset the external monitor by a couple hundred pixels before I run out of virtual desktop.

Is there anyway to use the external monitor as a completely different desktop? X 0:1?

thanks!

---

### Post by osx424242 on 2008-04-07
I had to increase the "Virtual" line in my Xorg.conf.  See [http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950) for more details.  It seems to be working fine on my panv3.  Then I use scripts similar to the ones from this thread: [http://ubuntuforums.org/showpost.php?p=4140658&postcount=291](http://ubuntuforums.org/showpost.php?p=4140658&postcount=291)

---

### Post by TheBuzzSaw on 2008-04-10
I am interested in knowing as well. I would like to have multiple desktops with my Daru2.

---

### Post by imhavoc on 2008-04-10
> **TheBuzzSaw said:**
> I am interested in knowing as well. I would like to have multiple desktops with my Daru2.

TBS,
I did figure out that, if you set the second monitor to --below, you get effectively two monitors... but it's just kinda weird to scroll off the bottom of one screen to get to the second monitor... I assume I'll get used to it.

I chose to go with --below because all my icons auto-align to the top of the screen. I had to move my KDE bar to the top of the screen -- which is kinda unnatural and creepy after driving KDE for 7 years. ;) If you leave the KDE bar at the bottom of the screen, it shows up at the bottom of the second screen. If you set the second screen to --above, the desktop icons move to the second screen....

It'll do for now.

---

