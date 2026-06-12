---
title: "Hearts of Iron: Armageddon is sluggish"
date: 2009-05-22
forum: Wine
---

### Post by MadCatmkII on 2009-05-22
I installed this a couple of weeks ago and was quite pleased to see that the installer works (except for the fact that it takes something like a minute for it to copy a single file).

Unfortunately the game runs like a snail. The mousepointer for example feels like it's tied to the mouse-position with a piece of elastic string and things like animations feel like they happen a second or so later than they ought to. So what I'd like to know is, what can I do to tweak this (if anything)?

My system:

Ubuntu 9.04
Ati x1950x (legacized, running the radeon driver)
Wine 1.1.21 (installed straight from the winehq repo)
When running the game, I have wine set to act like XP with a virtual desktop of 1024*768 (I have tried running it without the desktop in fullscreen and that made no noticeable difference). 
No dll-substitutions and no registry hacks
Sound through ALSA with standard settings

When I launch the game, this is output to the terminal:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x309ef94,0x00000000), stub!
fixme:gl_compat:add_gl_compat_wrappers GL implementation supports GL_ARB_fragment_program but not GL_EXT_fog_coord
fixme:gl_compat:add_gl_compat_wrappers The fog coord emulation will most likely fail
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
```

Any thoughts?

---

### Post by asdfoo on 2009-05-22
> **MadCatmkII said:**
> I installed this a couple of weeks ago and was quite pleased to see that the installer works (except for the fact that it takes something like a minute for it to copy a single file).

Unfortunately the game runs like a snail. The mousepointer for example feels like it's tied to the mouse-position with a piece of elastic string and things like animations feel like they happen a second or so later than they ought to. So what I'd like to know is, what can I do to tweak this (if anything)?

My system:

Ubuntu 9.04
Ati x1950x (legacized, running the radeon driver)
Wine 1.1.21 (installed straight from the winehq repo)
When running the game, I have wine set to act like XP with a virtual desktop of 1024*768 (I have tried running it without the desktop in fullscreen and that made no noticeable difference). 
No dll-substitutions and no registry hacks
Sound through ALSA with standard settings

When I launch the game, this is output to the terminal:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x309ef94,0x00000000), stub!
fixme:gl_compat:add_gl_compat_wrappers GL implementation supports GL_ARB_fragment_program but not GL_EXT_fog_coord
fixme:gl_compat:add_gl_compat_wrappers The fog coord emulation will most likely fail
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
```

Any thoughts?

Well, ignoring the video card + driver situation, have you tried using Wine 1.1.21? [http://winehq.org/download](http://winehq.org/download)

---

### Post by MadCatmkII on 2009-05-22
> **MadCatmkII said:**
> 

My system:

**Wine 1.1.21 (installed straight from the winehq repo)**



;)

---

### Post by asdfoo on 2009-05-22
> **MadCatmkII said:**
> ;)

oops :)

Not sure then, is there a demo available? I could test to see if it's also slow on nvidia.

---

### Post by NightMKoder on 2009-05-23
> **MadCatmkII said:**
> I installed this a couple of weeks ago and was quite pleased to see that the installer works (except for the fact that it takes something like a minute for it to copy a single file).

Unfortunately the game runs like a snail. The mousepointer for example feels like it's tied to the mouse-position with a piece of elastic string and things like animations feel like they happen a second or so later than they ought to. So what I'd like to know is, what can I do to tweak this (if anything)?

My system:

Ubuntu 9.04
Ati x1950x (legacized, running the radeon driver)
Wine 1.1.21 (installed straight from the winehq repo)
When running the game, I have wine set to act like XP with a virtual desktop of 1024*768 (I have tried running it without the desktop in fullscreen and that made no noticeable difference). 
No dll-substitutions and no registry hacks
Sound through ALSA with standard settings

When I launch the game, this is output to the terminal:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x309ef94,0x00000000), stub!
fixme:gl_compat:add_gl_compat_wrappers GL implementation supports GL_ARB_fragment_program but not GL_EXT_fog_coord
fixme:gl_compat:add_gl_compat_wrappers The fog coord emulation will most likely fail
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
```

Any thoughts?

That don't look too good. If the game uses a lot of the fog extension, sofware emulation might slow it down. The bigger culprit seems that the game tries to change to 16 bit resolution. Go into game options and set it to 32 bit (the X server isn't too keen about changing resolutions mid-run). In either case, see if turning off some graphics options helps.

---

### Post by MadCatmkII on 2009-05-23
There is a demo available [here]("http://www.fz.se/filer/?id=1465").


> **NightMKoder said:**
> That don't look too good. If the game uses a lot of the fog extension, sofware emulation might slow it down. The bigger culprit seems that the game tries to change to 16 bit resolution. Go into game options and set it to 32 bit (the X server isn't too keen about changing resolutions mid-run). In either case, see if turning off some graphics options helps.

I can see how that might cause some slowdowns. It's just that, well... It's a very 2d-game. It's all pixel-graphics and I've never seen a hint of any fog-effects. And the game doesn't have any graphics settings (One size fits all!) :?

---

### Post by YokoZar on 2009-05-23
I remember this game being slow a couple years ago when I last played it, though I can't remember if I got it to work right.

I do suggest the 32 bit color tweak though, converting between the two is a surprisingly expensive process.

---

### Post by MadCatmkII on 2009-05-23
How would I go about changing the colour-depth, though? Since the game doesn't give me that option, can I somehow force wine to do it?

---

### Post by asdfoo on 2009-05-23
> **MadCatmkII said:**
> How would I go about changing the colour-depth, though? Since the game doesn't give me that option, can I somehow force wine to do it?

colour-depth is handled by the X server, it's set in Xorg conf, and you have to restart X to change depths.

---

### Post by MadCatmkII on 2009-05-24
Well, that may present some new learning opportunities for me. You see, my xorg.conf looks like this:

```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

It doesn't feel quite as informative as I remember xorgs being in the past...

---

