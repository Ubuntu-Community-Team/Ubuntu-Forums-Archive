---
title: "Plea for easy screen resolution"
date: 2007-10-23
forum: Ubuntu Brainstorm
---

### Post by mpgarate on 2007-10-23
I myself have figured out just by clicking around how to get my screen resolution set, but its harder than it needs to be. for some reason, my monitor is not auto detected. It detects a dell monitor with some model number (mine is dell, dont know the #) but the ONLY screen resolution options are too low

I have to click on different screen resolutions until I see the screen resolution i know to be mine (1280x1024)

I think many 'noobs' would struggle with this, and is definitely an area for improvement in herdy heron (I still wish it were hungry hippo... sigh...)

---

### Post by screaminj3sus on 2007-10-23
Mine detects the resolution but not the refresh rates correctly, I think displayconfog-gtk is easy enough to use though. The gnome tool is pretty much useless with an nvidia card for refresh rates. It detects them incorrectly.

---

### Post by Pierre Lourens on 2007-10-23
> **screaminj3sus said:**
> Mine detects the resolution but not the refresh rates correctly, I think displayconfog-gtk is easy enough to use though. The gnome tool is pretty much useless with an nvidia card for refresh rates. It detects them incorrectly.

I agree that refresh rate is a problem on various LCDs, especially when connected to a TV-type LCD.

---

### Post by fnjordy on 2007-10-24
I think much like NetworkManager and wireless card drivers, the existence of a user-space graphical tool to control screen resolution will cause all the driver developers to sort out their issues and standardize on a system that works (xrandr).

It's pretty safe to say that future updates for nVidia and other chipsets will fix these problems.  Although presumably we will still have a choice between displayconfig-gtk and nvidia-settings / ati control panel, they shouldn't break the desktop.

---

