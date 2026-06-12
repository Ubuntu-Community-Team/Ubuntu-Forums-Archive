---
title: "problem with ubuntu 7.10 server"
date: 2008-04-15
forum: Server Platforms
---

### Post by nickpsal on 2008-04-15
I have install the ubuntu 7.1 server edition to my computer the installation finish but i can get into graphical mode it only work dos mode.
Please help beacuse i am new in linux!!!

---

### Post by kerry_s on 2008-04-15
the server does not have a gui, it's a command line system.

you can install one.
sudo apt-get install xorg gdm synaptic fluxbox menu
sudo update-menus
reboot(press ctrl+alt+delete)

log in open synaptic and get what ever else you want for your gui.

---

### Post by ibutho on 2008-04-15
The server edition does not install a GUI by default (most Unix server admins don't use GUIs). If you need a GUI, then run aptitude and install ubuntu-desktop e.g.
```
sudo aptitude update
sudo aptitude install ubuntu-desktop xserver-xorg
```
If you prefer KDE, install kubuntu-desktop and if you prefer XFCE install xubuntu-desktop instead of ubuntu-desktop.

---

### Post by cocotu on 2008-04-15
Linux servers are meant to be command line only, but you can always install a GUI.  I have not try that yet, ibutho is this reliable and secure?

---

### Post by FakeOutdoorsman on 2008-04-15
kerry_s' recommendation would install what you need to get a minimal GUI, but ibutho's will install everything that is on a standard Ubuntu desktop install, which I doubt you need.

You might be interested in Webmin.  It will allow you to configure your site graphically via a browser without you needing to install the extra baggage a GUI will bring.

---

### Post by nickpsal on 2008-04-16
thanks for your help

---

### Post by hyper_ch on 2008-04-16
what do you need a gui for on a server?

---

