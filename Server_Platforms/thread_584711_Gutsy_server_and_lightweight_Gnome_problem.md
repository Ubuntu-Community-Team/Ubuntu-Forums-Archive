---
title: "Gutsy server and lightweight Gnome problem"
date: 2007-10-21
forum: Server Platforms
---

### Post by ginjabunny on 2007-10-21
I am trying to move from 7.04 to 7.10 server amd64, on the old one I put a basic Gnome on it so I could use vino for remote desktop and run certain apps on it, but when I install the same set of packages on 7.10 then there seems to be something missing, all windows do not have a title bar and cannot be resized or moved. As the themes do not work and appearance app is unuseable then I installed everything I could find to do with themes and windows but with no change. I have instaled it twice with the same result.

The basic packages are I installed are
x-window-system-core gnome-core gdm gnome-media gnome-system-monitor gnome-system-tools gnome-volume-manager gnome-utils gnome-app-install synaptic

On 7.04 these were enough but it looks like some window manager functions may have been moved to another package or missed out!

I also tried gnome-desktop-environment which didn't fix it (but this installed lots of stuff I didn't want).

Has anypone else tried this, any ideas what I'm missing?

Help
_!!_

---

### Post by ginjabunny on 2007-10-21
I just discovered something, after I installed a third time just using packages - xorg gdm gnome - and the window problem is still there until I  went into the Appearance app on the visual effects tab and change it from none to normal and it complained about compiz not being there and when set back to normal then the window title bar and resizers have now appeared and are still there after a reboot. 

It seems that something it set incorrectly by default and fiddling with the visual effects has fixed it (hopefully). 

Seems to be working ok now, I may go back and try a more minimal install.

_!!_

---

### Post by ginjabunny on 2007-10-21
I went back to the original minimal lightweight install and changing the visual effects from none to normal and back fixes the window problem, it does it on a per user basis so probaby a setting stored somewhere in the users profile. I installed themes for gdm, gnome and ubuntu human to stop it complaining they weren't there.

Hopefully this will help others who encounter this problem.

Should I report this as a possible bug?

_!!_

---

