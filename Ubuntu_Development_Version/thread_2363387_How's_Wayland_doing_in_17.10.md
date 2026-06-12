---
title: "How's Wayland doing in 17.10?"
date: 2017-06-09
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-06-09
I'm finding Gnome with Wayland in 17.10 somewhat slow. How is it working with your install? My 17.10 didn't come with Unity.

---

### Post by #&amp;thj^% on 2017-06-09
For myself Wayland works as good as X11. Crisp and Snappy.
How ever there are still some issues with opening some GUI's as root, but there is also some work-arounds for that.
Been using it as a daily driver for a couple of days now!
EDIT: I have also started some personal tweaks I like...and running solid, so far!

---

### Post by rrnbtter on 2017-06-09
Greetings,
I'm using the updated Gnome-Wayland Desktop.  My system is using xwayland-server. I have yet to see any indication that there is a wayland-client on 17.10. But regarding your OP question, what is there is very good and much crisper than the Unity desktop that I have been using for the last six years. I can verify the issues noted in post #2 and I am sure that with the current concoction of xwayland and xorg and lightdm and gdm and x11 apps and etc there will be issues.  Overall I am satisfied with what I have even in this development stage.

---

### Post by arnold8969 on 2017-06-11
I also have issues with becoming Root. In regular Gnome it's okay.

---

### Post by ventrical on 2017-06-12
On some of my nVidia based installs xwayland/wayland seem to be snappier than usual. (non-nvidia driver based)

wayland session at login on intell based graphics will go to black-space using lightdm.

So some of the major bugs will be lightdm,gdm and wayland session logins.

Has anybody tried an install using nomodeset?

Regards..

---

### Post by ventrical on 2017-06-12
The daily is now called artful-desktop.

regards..

---

### Post by Frogs Hair on 2017-06-12
I have a white border around the gnome terminal in the Wayland session as of 6-12. This is a 17.04 upgrade.

---

### Post by ventrical on 2017-06-12
> **Frogs Hair said:**
> I have a white border around the gnome terminal in the Wayland session as of 6-12. This is a 17.04 upgrade.

I am noticing that several of my 17.04-17.10 upgrades are not up to par with what the current daily is displaying from a fresh install and live session.

---

### Post by amano on 2017-06-13
> **Frogs Hair said:**
> I have a white border around the gnome terminal in the Wayland session as of 6-12. This is a 17.04 upgrade.

That should be bug [https://bugs.launchpad.net/ubuntu-gnome/+bug/1650395](https://bugs.launchpad.net/ubuntu-gnome/+bug/1650395) which is tagged to be triaged for artful. 

As far as I understand the transparency for gnome-terminal isn't officially supported by Gnome and has to be patched in by the distros themselves. The way Fedora does it still works. The way Ubuntu does it is currently broken.

So someone (Jeremy?) would have to look at the proper Fedora patch and port it over to Ubuntu. Or just remove the transparency patch and put gnome-terminal to the officially supported state (without transparency, but still better than with artifacts).

---

### Post by Frogs Hair on 2017-06-13
> **amano said:**
> That should be bug [https://bugs.launchpad.net/ubuntu-gnome/+bug/1650395](https://bugs.launchpad.net/ubuntu-gnome/+bug/1650395) which is tagged to be triaged for artful. 

As far as I understand the transparency for gnome-terminal isn't officially supported by Gnome and has to be patched in by the distros themselves. The way Fedora does it still works. The way Ubuntu does it is currently broken.

So someone (Jeremy?) would have to look at the proper Fedora patch and port it over to Ubuntu. Or just remove the transparency patch and put gnome-terminal to the officially supported state (without transparency, but still better than with artifacts).

Thank you for the info !

---

### Post by Frogs Hair on 2017-06-13
Problem solved via gnome terminal updates.

---

