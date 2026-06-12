---
title: "Glitchy drop downs and drag and drop elements"
date: 2022-01-19
forum: Ubuntu/Debian BASED
---

### Post by anuragrao on 2022-01-19
Hi! I hope you're having a fantastic day. 
General Information: 
I'm running Pop_OS on an AMD Ryzen 3 3200G Processor. I freshly installed Pop_OS 20.10 and installed kde through ```
sudo apt install kde-standard
``` I installed all my required apps and everything is running incredible well except for one thing...
Problem: 
In some applications like signal-desktop, stable version of chromium etc., the drop down menus and drag and drop elements turn glitchy. They are not readable and have pinkish violent lines. I don't know how to put it in words exactly, so I'll attach a photo of it. 
Steps I've tried: 
I've tried changing the compositor to xrander and openGL 3, none of which worked. As for the glitchy drop downs on chromium, I added the chromium beta ppa to apt and upgraded. That solved the issue on chromium. For signal-desktop, both flatpak and snap versions of the app show the same behavior. 

Genuinely appreciate any support! 

Image: [COLOR=#FFFFFF][FONT=&amp]https://imgur.com/3SgCSIk[/FONT][/COLOR]

---

### Post by howefield on 2022-01-19
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by him610 on 2022-01-20
The repositories have two drivers for AMD graphics chips, one is *radeon* and the other is *amdgpu*. I would think you should probably have the *radeon* driver for your integrated graphics. If you have the incorrect driver installed the results may look weird.  Which do you have installed? Please show results of...
```
inxi -G
```

---

### Post by anuragrao on 2022-01-20
output of inxi -G:
```

[FONT=monospace][COLOR=#5454FF]**Graphics:  Device-1:**[/COLOR][COLOR=#000000] Advanced Micro Devices [AMD/ATI] Picasso [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] amdgpu [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel  [/COLOR]
           [COLOR=#5454FF]**Device-2:**[/COLOR][COLOR=#000000] SunplusIT ZQ-1080 HD camera [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] USB [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] snd-usb-audio,uvcvideo  [/COLOR]
           [COLOR=#5454FF]**Display:**[/COLOR][COLOR=#000000] x11 [/COLOR][COLOR=#5454FF]**server:**[/COLOR][COLOR=#000000] X.Org 1.20.13 [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#5454FF]**loaded:**[/COLOR][COLOR=#000000] amdgpu,ati [/COLOR][COLOR=#5454FF]**unloaded:**[/COLOR][COLOR=#000000] fbdev,modesetting,vesa  [/COLOR]
           [COLOR=#5454FF]**resolution:**[/COLOR][COLOR=#000000] 1920x1080~60Hz  [/COLOR]
           [COLOR=#5454FF]**OpenGL:**[/COLOR][COLOR=#5454FF]**renderer:**[/COLOR][COLOR=#000000] AMD Radeon Vega 8 Graphics (RAVEN DRM 3.42.0 5.15.11-76051511-generic LLVM 12.0.1)  [/COLOR]
           [COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 4.6 Mesa 21.2.2 [/COLOR]

[/FONT]
```

Thanks for the support

---

### Post by him610 on 2022-01-20
Hmm, you are using the amdgpu driver.
What does it look like when you boot from the installation medium (DVD or USB stick?) Does it look normal, or does it still look weird?

---

### Post by anuragrao on 2022-01-21
The same behavior is unfortunately observed in the live boot too. One thing to note is that this is observed only in the snap package of Chromium and both snap and flatpak packages of signal-desktop. Attaching more photos of the live boot: [https://imgur.com/a/o7IVbhG](https://imgur.com/a/o7IVbhG)


Edit: I also just noticed that the same thing is observed even in the snap package of spotify while dragging and dropping songs.

---

### Post by him610 on 2022-01-21
I don't use kde, signal-desktop, flatpaks, or snaps. Your attachments all look perfectly normal to me. Does the dog belong to you? 
Isn't Pop_OS based on Gnome? Then you installed KDE on top of the Pop_OS. Go back to the basic distribution and see if you still have the same issues. Avoid using flatpaks and snaps. Other than that, I am out of ideas.
Good luck.

One more thing, did you give the integrated graphics chip enough shared memory? You might want to give it the maximum allowed.

---

### Post by anuragrao on 2022-01-22
I did try using using the same apps on gnome (the native version of pop - pop-desktop). The exact same thing happened. I avoid snap and flatpak packages too but unfortunately those were the only packages available for the programs that I needed. The same effect was seen on the live boot environment too. Thanks for your suggestion on giving the graphics chip enough shared memory, I'll try that and get back here if that solved the problem :)

---

### Post by anuragrao on 2022-01-22
I checked the allocated memory to the integrated graphics in the BIOS and it is maxed out. Looks like it's a bug with pop-os itself. I will report it. Thanks for your support!

---

