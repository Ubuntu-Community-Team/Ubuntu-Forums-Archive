---
title: "nvidia-prime switching, log out fails"
date: 2017-04-29
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-04-29
If using nvidia-prime when switching Gpu's one is prompted to log out/in to effect switch
This will not work in UbuntuGnome as - 
xorg.conf is not removed or created as need be.
It appears update-alternatives is not run, not sure there..

A restart is required to switch

---

### Post by jbicha on 2017-04-29
If you are using Ubuntu GNOME 17.04+, switcheroo-control is installed by default. If it works correctly, it's supposed to force your less powerful GPU to be used for your regular session, but you can [right-click]("http://www.hadess.net/2016/10/dual-gpu-integration-in-gnome.html") on apps to "Launch using Dedicated Graphics Card."

I don't think you need nvidia-prime any more if you are just using GNOME.

---

### Post by mc4man on 2017-04-29
> **jbicha said:**
> If you are using Ubuntu GNOME 17.04+, switcheroo-control is installed by default. If it works correctly, it's supposed to force your less powerful GPU to be used for your regular session, but you can [right-click]("http://www.hadess.net/2016/10/dual-gpu-integration-in-gnome.html") on apps to "Launch using Dedicated Graphics Card."

I don't think you need nvidia-prime any more if you are just using GNOME.
It would appear that's only for nouveau not nvidia prop drivers. 

Ot. Also in regards to a Wayland session there is no option to use if nvidia drivers are installed & for whatever reason in Ubuntu nvidia modesetting can not be enabled. 
Maybe that's behind no eglstreams support??

---

