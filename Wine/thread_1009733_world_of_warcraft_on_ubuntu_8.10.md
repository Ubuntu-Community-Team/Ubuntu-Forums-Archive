---
title: "world of warcraft on ubuntu 8.10"
date: 2008-12-12
forum: Wine
---

### Post by b.hunt96 on 2008-12-12
i've been trying to figure out how to get world of warcraft to work with Ubuntu 8.10 with wine. i've messed around with the config.wtf file but it hasn't really worked out to well. when i open WoW it looks as if everything got smashed together. graphics blend and text overlaps. its incomprehensible.

i'm very new to this whole linux thing. any help would be greatly appreciated.

---

### Post by hikaricore on 2008-12-13
Video hardware info?
Which driver are you using?
Did you follow any install guides?
What version of WINE are you running?
Did you install it from the ubuntu repo or the winehq repo?

Please provide more information.

---

### Post by Leafer on 2008-12-13
Right click the icon Wine placed on your desktop.
Find the Command line. At the end of it put:
-opengl

Then try it.

---

### Post by b.hunt96 on 2008-12-13
video: intel Mobile 915GM/PM/GMS/910GML

i'm not sure how to check the video drivers ubuntu.

i did follow a couple of install guides that i found on other forums. things like changing the config.wtf file to use openGL and actually using wine to open wow. i'm using wine 1.0.1 and i got it from winehq.

---

### Post by Muffinabus on 2008-12-13
[http://img.photobucket.com/albums/v109/tmm_xiv/DSCN0231.jpg](http://img.photobucket.com/albums/v109/tmm_xiv/DSCN0231.jpg)

Does it look anything like this?

That's what mine did when I didn't have my video drivers properly installed... at least I think that's what it was.

---

### Post by Ameneon on 2008-12-13
Sounds like I've been unreasonably lucky, I didn't have to follow a single guide (did look at them, but didn't need any of the instructions), just downloaded the installers and ran one after the other. Had no joy in crossover (couldn't get the darn "agree" button in the EULA to be clickable) but in wine it all worked without a hitch. Only thing is that I can't run from the wine start menu link as it loops in an endless "downloaded tools" cycle, but works just dandy when starting from the wow.exe file itself.

What exact problems are you having? IE, is it failing installation? If so, at what point?

---

### Post by Ameneon on 2008-12-13
Oh sorry, see now that you mentioned the problem being with the video.

---

### Post by Muffinabus on 2008-12-13
> **Ameneon said:**
> Sounds like I've been unreasonably lucky, I didn't have to follow a single guide (did look at them, but didn't need any of the instructions), just downloaded the installers and ran one after the other. Had no joy in crossover (couldn't get the darn "agree" button in the EULA to be clickable) but in wine it all worked without a hitch. Only thing is that I can't run from the wine start menu link as it loops in an endless "downloaded tools" cycle, but works just dandy when starting from the wow.exe file itself.

What exact problems are you having? IE, is it failing installation? If so, at what point?

Same here, I didn't use a single guide, double clicking the .exe on my Windows drive has the game run beautifully, heh.

---

### Post by b.hunt96 on 2008-12-13
well, i tried switching it from opengl to direct3d and suprisingly the graphics show up. there are still glitches but at least i can see where i am going in game lol.

the problems i'm having now are very low fps, about 4 to 5 fps in ogrimmar, and small graphic glitches. i'm more worried about the fps though. any ideas? was it a bad idea to switch bad to direct3d?

---

### Post by cmmckoy on 2008-12-20
I'm also using Ubuntu 8.10, and my graphics were very jumbled when the log-in screen was initiated, and when I fixed that problem, it would only do it half the time, the other half I could get into the game but all the graphics were jumbled once I got in.  I went into 'Configure Wine', and in the Graphics tab, I selected the option to emulate a virtual desktop, which made in load into a window, which fixed 99% of the video problems (the only issue I'm getting now is that when I'm inside my minimap turns white), if you're still having any problems with graphics being messed up you may want to try that, not sure if it will help, but I thought I'd throw my two cents in.

Hope this helps.

---

