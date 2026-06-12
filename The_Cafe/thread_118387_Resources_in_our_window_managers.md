---
title: "Resources in our window managers"
date: 2006-01-16
forum: The Cafe
---

### Post by otake-tux on 2006-01-16
I'm a big fluxbox fan.  I have always tried to use as little resources as possible.  I just like efficiency.  Recently I upped the ram on my laptop which is running ubuntu with fluxbox as my main window manager / desktop.  

In fluxbox, everything is really fast as long as you dont load any program that uses the gnome libraries or the kde libraries (gtk+ , Qt ).  Any program that uses those libraries loads really slow because it needs those libraries.  If I was running gnome the same program would load faster because the gtk+ libraries are allredy loaded. So whats the real benefit of using fluxbox over kde or gnome?

specs: 768 mb RAM, pentium 4 CPU.

---

### Post by DoorGunner on 2006-01-16
Comparitively speaking gnome and kde are very fat (phat) programs (everything you need and highly automated). They are designed for ease of use. Anyone can use these desktops and enjoy them, configure them with ease.

Fluxbox on the otherhand is leaner and requires less physical space. In the end fluxbox will have less features the gnome and kde. It is less frilly as a result. It tends to be more for the intermediate to advanced users. However, is very accomodating to those who require less hard drive space or have resourse challenged machines.

For the intermediate and advanced user it can be programed to take on many different forms. In this i mean it can be programmed to look the way you want it to.

I run it anyways cause i like it and can learn while using it.

One thing you could try is a program called prelinker. It helps to speed things up by prelinking libraries to applications.....or at least that is the way i think it works........(speeding up those pesky gnome and kde programs)
[http://ubuntuforums.org/archive/index.php/t-74197.html](http://ubuntuforums.org/archive/index.php/t-74197.html)

---

### Post by prizrak on 2006-01-17
You could try XFCE it's also GTK+ based so Gnome apps don't take long to load, and it is also alot less resource intensive than either of "big" GUI's. Gnome with XFWM as a WM seems to run almost as fast but then again I have fairly decent hardware.

---

### Post by poofyhairguy on 2006-01-17
[QUOTE=otake-tux].  If I was running gnome the same program would load faster because the gtk+ libraries are allredy loaded. So whats the real benefit of using fluxbox over kde or gnome?
[/QUOTE]

It does not load all the other KDE and Gnome things. For example Gnome loads gnome-settings-daemon (which give apps the GTK2 look amoung other things) and gnome-volume-manager (which puts pen drives and whatever on your desktop). Fluxbox does not.

---

