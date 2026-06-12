---
title: "Winecfg trouble"
date: 2009-05-18
forum: Wine
---

### Post by Shindogo on 2009-05-18
Basically, my winecfg fonts are huge, and I emulate a windows desktop. So since I can't scroll the window, I can't see all the options, which is quite frustrating. I've included a screenshot to show what I mean.

Can anyone help with this? Thanks.

---

### Post by YldGuy on 2009-05-18
> **Shindogo said:**
> Basically, my winecfg fonts are huge, and I emulate a windows desktop. So since I can't scroll the window, I can't see all the options, which is quite frustrating. I've included a screenshot to show what I mean.

Can anyone help with this? Thanks.


my first thoughts are that the dpi settings are changed. i don't have a way to check it now on my laptop but what you can do is:

1) move the window around by pressing "ALT+Left Mouse Button" over that winecfg window.

2) There is a dpi settings in there somewhere. Should be in Display tab (if there is any) or Graphics tab. Not sure, but the idea is to find that dpi settings and change it back to 96.

---

### Post by Shindogo on 2009-05-19
Thanks for the tip, but I can't move the window because it's in the emulated DE window, so alt+click just moves that window around on my real desktop. Any other suggestions?

---

### Post by YldGuy on 2009-05-19
> **Shindogo said:**
> Thanks for the tip, but I can't move the window because it's in the emulated DE window, so alt+click just moves that window around on my real desktop. Any other suggestions?

hmm.. i am giving it a really wild shot here.

i assume that you have enabled a virtual desktop for wine. first we will go about disabling it. i am referring this ([http://www.cyberpunkcafe.com/images/vlshots/step4graphics.jpg](http://www.cyberpunkcafe.com/images/vlshots/step4graphics.jpg)) for the winecfg screen, since i don't have my laptop around.

as you see, the desktop settings are in the graphics tab. From your screenshot i guess you can go to the graphics tab. It would take exactly three tabs to reach the virtual desktop checkbox while on graphics tab. press Spacebar to uncheck it. press Enter  key to save it. then try restarting winecfg. i hope by this time you will get it out of a DE and move it around by alt+click. just try.

There must be some configuration file settings which could do the same but I am not an expert to do that.

---

### Post by cogadh on 2009-05-19
> **Shindogo said:**
> Basically, my winecfg fonts are huge, and I emulate a windows desktop. So since I can't scroll the window, I can't see all the options, which is quite frustrating. I've included a screenshot to show what I mean.

Can anyone help with this? Thanks.
You just have the DPI set too high. Open the ~/.wine/system.reg file with a text editor and look for this section:
```
[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts] 1209080331
"FIXEDFON.FON"="vgafix.fon"
"FONTS.FON"="vgasys.fon"
"LogPixels"=dword:00000060
"OEMFONT.FON"="vgaoem.fon"
```
The important line is **"LogPixels"=dword:00000060**. I'm not sure what yours will say, but if you change yours to match that line, font size will be reset to 96 DPI (which is what it normally is).

---

### Post by Shindogo on 2009-05-19
Problem solved, thanks very much to both.

---

