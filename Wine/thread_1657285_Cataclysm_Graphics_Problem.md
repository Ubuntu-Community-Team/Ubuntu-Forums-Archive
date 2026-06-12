---
title: "Cataclysm Graphics Problem"
date: 2011-01-01
forum: Wine
---

### Post by Sushi1091 on 2011-01-01
Hi, I am currently running wine 1.3.10, and to run World of Warcraft: Cataclysm. Now I used to run in it windows till I decided to make my laptop more Linux oriented. I currently have an ASUS N61Jq, which has Intel Core i7-720QM, ATI Mobility Radeon HD 5730, and 4 GB of RAM. On windows I was able to run Good graphics with this exact same laptop, however once switching to Ubuntu 10.10 I can not bump my graphics above low. Also my sound doesn't work... Now I am not sure what to do here, I have searched everywhere online (Googled it in different ways) and found nothing helpful. I have gone into the config.wtf file and added the opengl, and sound bits and I still have poopy graphics settings, plus no sound. If anyone has any idea as to why I can not improve the quality of graphics in wine or any solution it would be greatly appreciated. Thanks for your time.

---

### Post by cwwilson721 on 2011-01-01
You haven't searched much. This forum has all you need.

Reason for lower graphics is opengl. WoW doesn't like it, so most 'eyecandy' is off in opengl.

Make sure you have whatever the latest drivers for your ATi card/chip is installed.

As for sound, run WoW in a XP setting, not Vista or Win7. And make sure in winecfg that you use alsa, no other sound types.

---

### Post by LauraSakura on 2011-01-01
Don't be afraid to try it once without the -opengl flag. For some computers (mine included), it works just fine in D3D Mode.

---

### Post by Sushi1091 on 2011-01-01
Well, After undoing the opengl flag the other graphic options did become available however fps suffered greatly on my laptop, So I went to add the opengl flag in the wow config file "SET gxAPI "OpenGL"" and I now am recieving the message Failed to find suitable display driver exiting program after I click play in the loader.

Little confused...

---

### Post by Tweak42 on 2011-01-04
To isolate whither it's WoW or the opengl driver is the problem, try running glxgears from the command line. It's part of the mesa-utils if you don't have it installed.

If glxgears runs, then something is probably amiss in the config.wtf file.  Backup the file and try with a clean one, using the -opengl switch only.

If glxgears doesn't run, then something is wrong with the radeon opengl driver.  I'm only familiar with nvidia so someone Ati experience would have a better clue where to troubleshoot.

---

