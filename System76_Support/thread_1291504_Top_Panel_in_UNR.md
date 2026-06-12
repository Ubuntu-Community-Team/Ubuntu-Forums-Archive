---
title: "Top Panel in UNR"
date: 2009-10-14
forum: System76 Support
---

### Post by Eyore15 on 2009-10-14
When booting in UNR on my starling, the top panel that shows date, time, speaker status, connectivity, and battery status, is missing. I do know the network is connecting  --  Firefox connects properly.

If I go to preferences and change to standard view, the panel is there.

If I change a second time, back to UNR, the panel returns.

I'd prefer to be able to boot the first time in UNR with the top panel in place.

TIA

mcm

---

### Post by thomasaaron on 2009-10-15
Just out of curiosity, does this happen if you disable desktop effects? I've seen the problem the other way around before (no panel in the standard desktop) and that seemed to get it back on track.

Prefs > Appearance > Visual Effects > None

---

### Post by Eyore15 on 2009-10-15
Visual effects has been set to none throughout this time.  It was set that way from the factory and I never changed it.

I just booted again a few moments ago with the same effect; no panel in UNR,change preferences to traditional look, change back, and panel is there.

---

### Post by thomasaaron on 2009-10-15
This is a bit of a long shot, but go to Preferences > Startup Applications and click the Options tab. Make sure the checkbox is NOT selected.

---

### Post by Eyore15 on 2009-10-15
> **thomasaaron said:**
> This is a bit of a long shot, but go to Preferences > Startup Applications and click the Options tab. Make sure the checkbox is NOT selected.

I double checked; the checkbox is not selected.

I haven't changed anything from the way it came out of the box.  Everything worked fine until I changed to classic desktop the first time.  Since then the problem has persisted.  I've had the computer shutdown several times since the problem began, and it is always the same.  Boots to UNR without the top panel, switch to classic and the top panel appears, switch back to UNR and the top panel is there.

Don't know if is related, but I just had to go into "printers"; only about half the window showed on the screen (in the upper left-hand corner).  The top panel of the "printer window" was missing so I couldn't close the window.  I finally got it off screen by opening classic view; that closed the open window.

mcm

---

### Post by thomasaaron on 2009-10-15
Run this command from a terminal

rm .config/gnome-session/saved-sessions/*

Then reboot.

---

### Post by Eyore15 on 2009-10-15
> **thomasaaron said:**
> Run this command from a terminal

rm .config/gnome-session/saved-sessions/*

Then reboot.

reply "no such file or directory"

---

### Post by thomasaaron on 2009-10-16
OK. I think this is related to this bug with the desktop switcher...
[https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519)

Please run this command...
gconftool-2 --recursive-unset /apps/panel
...and then reboot.

Did that fix it?

---

### Post by Eyore15 on 2009-10-16
> **thomasaaron said:**
> OK. I think this is related to this bug with the desktop switcher...
[https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519)

Please run this command...
gconftool-2 --recursive-unset /apps/panel
...and then reboot.

Did that fix it?

I'll let you know the first of the week.  I left my power cord at school and the batteries just died.  I can tell you that I couldn't run it from UNR; I had to run it from Classic. When I was shutting down I caught a brief glimpse of a series of error messages as the shutdown finished.

Thanks for your attention to this.

mcm

---

