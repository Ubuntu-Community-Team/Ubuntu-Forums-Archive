---
title: "Starcraft Doesn't Fullscreen, Opens Top-Left Hand Corner"
date: 2010-01-03
forum: Wine
---

### Post by Sugi on 2010-01-03
When I try to run Starcraft in fullscreen mode, the game opens and pops up in the top left hand corner.  It's looks like it's in a windows mode, but the rest of the screen is black.

Like this:
[http://img13.imageshack.us/img13/7905/screenshotopv.png](http://img13.imageshack.us/img13/7905/screenshotopv.png)

I can't seem to fix this problem at all.

Ubuntu 9.10 64 bit
Compiled Wine 1.1.27
Nvidia 260 GTX
Nvidia 185.18.36
Resolution 1920x1080

Tried with the following enable:
 - Force Full GPU Scaling (check and uncheck)
*Has no Effect at all

 - GPU Scaling Method - Stretched
*Has no Effect at all

 - GPU Scaling Method - Centered
*Has no Effect at all

 - GPU Scaling Method - Aspect Ratio Scaled
*Has no Effect at all

 - Added this to xorg
Option "ModeValidation" "NoVertRefreshCheck,NoHorizSyncCheck" 
*Has no Effect at all

 - Added this to xorg
*Break my X
Option "FlatPanelProperties" "Scaling = aspect-scaled" :"

 - Separate X for Starcraft *I can't get this to work for me.
[http://ubuntuforums.org/showthread.php?p=5144003](http://ubuntuforums.org/showthread.php?p=5144003)

Terminal Read0ut:
wine StarCraft.exe
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2f4,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x8 @0! (XRandR)
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8cc, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13ea78,0x147f40): stub

Thanks,
Sugi

---

### Post by beastrace91 on 2010-01-03
Try running Wine in either a virtual desktop or manually set your default desktop resolution to 640x480 - this should fix it right up.

~Jeff

---

### Post by Sugi on 2010-01-03
Sadly, I need some kind of fix, not a workaround.  Windows mode doesn't allow me to play Starcraft.  And changing the resolution changes the size of the every windows.  

Thanks for the tip though,
Sugi

---

### Post by Sugi on 2010-01-11
bump

---

### Post by beastrace91 on 2010-01-12
> **Sugi said:**
> bump

Try different Wine versions. Thats always a good bet - or because Starcraft is so old personally I run the game from a Windows XP VM to get full usage out of the game.

~Jeff

---

### Post by Sugi on 2010-01-12
I actually tried it in a VM and it was pitiful running that way, but then again I like pro-starcraft.  So speed is everything.

I actually tried Starcraft again through a clean installation instead a compiled wine and it worked.  Odd :/  Everything is working now, even stretched view of Starcraft on a widescreen monitor, but the only problem is the mouse is way too sensitive and scrolling is too slow. :/

Sugi

---

