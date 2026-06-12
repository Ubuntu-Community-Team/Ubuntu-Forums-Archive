---
title: "installing server and gnome with out garbage"
date: 2009-06-19
forum: Server Platforms
---

### Post by Eonasdan on 2009-06-19
if I install the server platform and then do

```
sudo apt-get install ubuntu-desktop
```it installs all the games and browsers and email clients and lots of other stuff I don't want. How do I install the gui without all of that?

---

### Post by tgalati4 on 2009-06-19
apt-cache search minimal

---

### Post by ghen on 2009-06-19
```
apt-get install xorg gdm gnome-core
```

Very minimal gnome interface. You get an error once on startup about something small not being installed (wasn't important enough to remember).

---

### Post by wojox on 2009-06-19
Type 

sudo aptitude install x-window-system-core gnome-core

Press enter

This installs a scaled down version of Gnome that keeps features to a minimum and saves system resources.

---

### Post by Eonasdan on 2009-06-19
awesome thanks guys. I'll give that I try. I'm using a virtual machine at the moment but we are hoping to install this on an actual server and run some of our hosting from it. An as Windows Server/SQL guys it's going to be a fun ride trying to figure out LAMP. :D

---

### Post by tgalati4 on 2009-06-19
When you install server, LAMP is running out of the box.  Not much to figure out except adding content and fiddling with a few configuration files.

Learning Linux may take some time though.

---

### Post by Cheesemill on 2009-06-19
> **ghen said:**
> ```
apt-get install xorg gdm gnome-core
```Very minimal gnome interface. You get an error once on startup about something small not being installed (wasn't important enough to remember).

I always do the following one-liner
```
sudo apt-get update && sudo apt-get -y install xorg && sudo apt-get -y install gdm gnome-core ubuntu-artwork fast-user-switch-applet && sudo shutdown now -r
```whenever I want to install a minimal GUI. The error your referring to is due to fast-user-switch-applet being missing.

---

### Post by Cheesemill on 2009-06-19
> **tgalati4 said:**
> When you install server, LAMP is running out of the box.  Not much to figure out except adding content and fiddling with a few configuration files.

Learning Linux may take some time though.

Only if you choose to install it on the tasksel screen.
I always select the minimum amount of packages possible during install and add LAMP afterwards by doing a:
```
apt-get install lamp-server^
```Chances are there are packages that will need upgrading on a clean install so you would end up having to downloaded updated versions of the LAMP stack components anyway.

---

