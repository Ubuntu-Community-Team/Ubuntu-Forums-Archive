---
title: "Unity: No Icons, No Sidebar, No Menus"
date: 2013-04-20
forum: Ubuntu Development Version
---

### Post by mooreted on 2013-04-20
I tried to install 13.04 from the x64 iso but that failed, so I installed 12.10 and upgraded to 13.04. I managed to get Nvidia-313 installed; direct-rendering is enabled so the driver is working. But, all I see is my wall paper. What I have tried:

setsid unity
dconf reset -f /org/compiz/
sudo -i dpkg --configure -a
sudo apt-get -f install

"use synaptic to purge the installed nvidia packages, drop the xorg.conf too if it exist, then install nvidia-313-updates"

Reinstalled ubuntu-desktop
Reinstalled unity
Reinstalled compiz

I guess I will have to install a wm for now.

---

### Post by mooreted on 2013-04-20
Um, ok. No idea what just happened. Been at this for hours and nothing worked. Now after a reboot, it's back.

I may have to spray for gremlins.

---

