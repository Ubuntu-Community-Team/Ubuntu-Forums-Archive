---
title: "Problems running starcraft and warcraft 3 with wine"
date: 2009-08-22
forum: Wine
---

### Post by KIAaze on 2009-08-22
Hi,

I managed to install starcraft and warcraft 3 ROC+TFT using wine-1.1.27.
Unfortunately, I have two problems:

1) Battle.net for Starcraft seems to work, but I only have white text on black background. The background images aren't there.
I haven't tried joining a game on it yet.

2) For Warcraft, everything works except the movies (I had to rename the Movies folder).
However, when I quit the game, I end back up at the login screen (the screen isn't just locked. I am completely logged out.)! (I use Kubuntu by the way).

Any ideas how to fix this?

---

### Post by cherva on 2009-08-22
StarCraft's Battle.net is a well known bug when you join a game everything returns to normal :)

---

### Post by KIAaze on 2009-08-22
Ah ok, so there nothing that can be done about it currently? :(

Well, as for the second bug, I haven't been able to reproduce it. Maybe my system was already a bit messed up because of all the previous tries getting the games to run. The resolution was already lowered at least (and is again now). :confused:

P.S:
Trying to run the same games in VirtualBox:
From what I've read it's not possible to run Warcraft 3 with VirtualBox due to missing 3D acceleration. Is that correct?
I installed it without problems, but when trying to run it it complains about an incorrect directX version despite me having directX 9.0c + 3D acceleration checked in the virtual machine settings. :/
(and starcraft doesn't fill the whole screen...)

---

### Post by cherva on 2009-08-23
VirtualBox has an experimental OpenGL support witch is not enough to play games at the moment. WarCraft uses DirecX witch is not supported by VirtualBox. About the WC3 bug sorry I don't play it. About SC I don't thing there is a solution .... you will have to play it like this for now. You can see the progress of the bug at wine's bug tracker here
[http://bugs.winehq.org/show_bug.cgi?id=2467]("http://bugs.winehq.org/show_bug.cgi?id=2467")

---

### Post by KIAaze on 2009-08-23
Thanks for the link to the bug report.
I tried changing my resolution to 640x480 before running starcraft, but that didn't change anything.
Anyway, other than that, I'm very happy at how well it runs. I think booting into Windows won't be necessary anymore. :P

---

### Post by NightMKoder on 2009-08-23
If you get knocked back to the login screen, it means xorg crashed and you probably have a problem with your video drivers.

If you want decent directx support in virtualbox, you might need to install wined3d.

---

