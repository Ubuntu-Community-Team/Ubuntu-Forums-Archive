---
title: "KDE4, multiple monitors, and a Panp4i"
date: 2009-12-25
forum: System76 Support
---

### Post by thebinaryblob on 2009-12-25
So I decided I wanted to try KDE4, and so far, I love it. Except for the fact that I can't figure out how to make my second display work as an extension of my desktop just like how I had it setup in gnome. Unfortunately, KDE's display settings has no way to set this (and the multiple monitors pane just says that I do not have a multiple monitor setup???), and gnome-display-settings has no effect on KDE (not much of a surprise though).

I saw another thread that was specific to setting multiple monitors up with NVIDIA cards, but my laptop has an Intel graphics card. It also used a bunch of commands and config file editing, I would like to know if there is a GUI tool for this.

As the title states, I have a PanP4i.
To be a little more clear, I am NOT trying to clone my displays.
Even if you don't know how to do it, any useful information would be welcome.

---

### Post by djurny on 2009-12-25
you could try an opensuse livecd, use 'sax2' (or whatever its called) to configure your dual displays and copy the resulting xorg .conf to a safe place :)

---

### Post by Derath on 2009-12-25
I will check this out later, when I can pull out my second monitor. Granted I have the nVidia chip on my panp4n, and the nVidia software works great to control this, I did see the "multiple monitor" menu in KDE's settings, I think you may have to connect it and use something to activate it, and then use KDE's settings to tell it to use extension rather than clone.

Will check later to verify.

---

### Post by thebinaryblob on 2009-12-25
I did figure it out, but the solution I found is a bit crude. Using an openbox (not an kde session with openbox) and then starting all of the kde stuff manually allows me to configure the screens with gnome-display-properties :) . All I have to do now is configure openbox.

If anyone does find out how to get this working in KDE, let me know :)

---

### Post by thomasaaron on 2009-12-26
Try running...

sudo apt-get install nvidia-settings

...and then, to configure your monitors, run...

sudo nvidia-settings

I *think* that should work on Kubuntu, but I'm not sure.

---

### Post by thebinaryblob on 2009-12-26
will nvidia-settings even work on a PanP4i? it has an intel graphics card, not an nvidia.

---

### Post by Derath on 2009-12-27
Dont think I have forgotten about you, I am meaning on testing this soon, I have an idea on it, I think you might have to identify the outputs on one of the other areas on KDE's menu, then configure multiple monitors, it's just been a little busy since I received large (meaning size) gifts this year and having to plan how to re-arrange a house to accommodate the new stuff.

---

### Post by thomasaaron on 2009-12-28
> will nvidia-settings even work on a PanP4i? it has an intel graphics card, not an nvidia.

CORRECT! I missed the 'i'. nvidia-settings won't work.

So, you should be able to detect and configure an external monitor via System > Prefs > Display in Gnome.

You can grab the rectangle representing the external monitor and drag&drop it to either the right or left of the laptop lcd's square. This should create a spanned desktop scenario.

---

### Post by betrunkenaffe on 2010-01-02
> **thomasaaron said:**
> CORRECT! I missed the 'i'. nvidia-settings won't work.

So, you should be able to detect and configure an external monitor via System > Prefs > Display in Gnome.

You can grab the rectangle representing the external monitor and drag&drop it to either the right or left of the laptop lcd's square. This should create a spanned desktop scenario.

I'm running Kubuntu 9.10 and went Applications->Settings->System Settings->Computer Administration section->Display

Should have option for multiple monitors there, I haven't used because I have panp4 with nvidia..

---

### Post by thebinaryblob on 2010-01-03
Unfortunately, when I use the KDE configuration program, it doesn't give me the option to set my monitors as anything other than clones. When I go to the section for multiple monitors, it says that I do not have a multiple monitor setup. Almost like one part can detect the second display, and the other cannot.

---

### Post by satsujinka on 2010-01-04
Can you give me the output of xrandr?

As an example, when I use two monitors I use the following command:
```
xrandr --output VGA1 --auto --output LVDS1 --auto --left-of VGA1
```

What this does is setup my laptop's monitor to the left of my external monitor. A similar command should work for you.

---

