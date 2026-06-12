---
title: "Pangolin external monitor troubles"
date: 2009-08-10
forum: System76 Support
---

### Post by marshmallow1304 on 2009-08-10
I'm trying to use an external 22" widescreen LCD monitor with my PanP5 (Jaunty, x64).  I plugged in the monitor via VGA, then used Fn+F7 to toggle output.  I get an image on the monitor, but the problem is that it doesn't seem to be sized properly.  On the external monitor, the whole of my desktop does not appear on the screen and the image scrolls to follow the mouse.  I've tried to configure with the NVIDIA settings tool, but I usually end up making it worse.

AFAIK, the problem has something to do with the fact that my external monitor doesn't support 1080x800 (the resolution of the Pangolin's screen).  The only viable option I've found so far is to (through the NVIDIA settings) disable the onboard screen and enable the external monitor.  This provides perfect results with any of the monitor's resolutions, but it's a bit of a pain.


Any suggestions?



[size=4]Edit: The new NVIDIA driver (185) handles the external monitor much better.[/size]

---

### Post by thomasaaron on 2009-08-11
First, nVidia settings is where you need to be configuring the monitors.

If you're trying to span/extend the monitors, the xserver creates a virtual resolution that envelops both screens. So, the resolution may look like it is off on one of the screens. (However, drag a window into it to see how well it is rendered. It might be right on the money.)

If you are just trying to use an external monitor, turning on the external and turning off the laptop's screen is the best way to go.

---

### Post by marshmallow1304 on 2009-08-11
I was initially just trying to clone the screen to the external monitor.  That always looks bad on one of the displays because the Gnome panels are the wrong size.  For now, I'm pleased with using one display at a time.  Maybe I'll try spanning later.

---

### Post by tlroche on 2009-10-03
How to set resolutions so as to enable full-screen display on both the builtin and external monitors, using the nvidia driver? Details:

I have a brand-new, shipped last week, PanP5 with
[LIST]
[*]graphics=512 MB DDR2 nVidia GeForce G105M
[*]driver=NVIDIA Accelerated graphics driver (version 180) (installed via System>Administration>Hardware Drivers)
[/LIST]
After I attach a VGA cable to both the PanP and an external monitor, and set the latter to take external source, I observe

[LIST=1]
[*]do Fn-F7 on the PanP:
[LIST]
[*]PanP screen goes dark
[*]external screen displays @ same resolution as PanP, but does not show full display. However display pans with mouse, so I can see all parts of the display on the external monitor by moving the mouse.
[/LIST]
[*]hit Fn-F7 again: both screens display, with same resolution
[LIST]
[*]PanP screen displays normally
[*]external screen displays/pans as in previous item
[/LIST]
[*]hit Fn-F7 yet again:
[LIST]
[*]PanP screen displays normally
[*]external screen gets no signal
[/LIST]
[*]hit Fn-F7 one more time: back to case# 1 above.
[/LIST]

> **thomasaaron said:**
> If you are just trying to use an external monitor, turning on the external and turning off the laptop's screen is the best way to go.

That looks good, but for presentation I'd like to be able to see my screen as well: I really dislike it when folks present with their backs to the audience, so I'd like to avoid doing that. I'd also like to be able to project the full screen under some circumstances.

---

