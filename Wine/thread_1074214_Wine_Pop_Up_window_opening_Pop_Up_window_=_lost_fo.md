---
title: "Wine Pop Up window opening Pop Up window = lost focus"
date: 2009-02-19
forum: Wine
---

### Post by tkornacki on 2009-02-19
Hello

I am running a program called Planimate under WINE (wine-1.1.14, winXP, with compiz controlling and decorating windows) and when the program the opens a pop up window everything is fine.  When the pop up window attempts to open a 2nd pop up window the focus is lost and the 2nd pop up closes.  It flashes briefly and then closes.

The problem is triggered when a pop up window triggers the opening of a second pop up window or pop up menu.

I am running Intrepid with Compiz 0.7.8. and an emerald theme.

I have tried various settings in the compiz manager but cant seem to get the 2nd pop up window to display and stay open.

If i disable the WINE option to allow the Windows default manager to control the windows then it works fine.  However, the windows then become sticky on all desktops and always remain on top of other windows.  Also, the window decoration is not applied (no biggy).

Can anyone suggest something i may try that could correct this issue?

---

### Post by cogadh on 2009-02-19
Turn off Compiz and switch to Metacity as the window manager. Wine and Compiz do not get along, so you usually need to disable it before running anything with Wine. From the [Wine FAQ]("http://wiki.winehq.org/FAQ"):
> **I'm using Desktop Effects with Compiz, Fusion, or XGL and get poor performance/odd messages/broken applications**

Using composite display managers in Linux tends to cripple OpenGL performance or break OpenGL entirely. We recommend that you disable them entirely before trying to use Wine. If you are using one and experiencing slow performance then please do not file bugs in Wine, as these are bugs in your window manager or your video drivers. Also, disabling the Composite extension within /etc/X11/xorg.conf will most certainly prevent any compositing from affecting Wine.

---

### Post by tkornacki on 2009-02-19
Cheers.

Running with metacity and the wine option disabled for allowing the window manager to decorate the windows has gotten around the problems i have been facing.  The performance has jumped significantly as well :-) using metacity.

Thanks for the help.

---

