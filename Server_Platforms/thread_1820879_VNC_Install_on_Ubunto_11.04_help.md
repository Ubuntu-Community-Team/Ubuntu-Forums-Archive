---
title: "VNC Install on Ubunto 11.04 help"
date: 2011-08-08
forum: Server Platforms
---

### Post by ManiKinG on 2011-08-08
hello need help,
 
i m trying to install VNC server on ubunto linux server via Putty ,
 
when i finish to install and login via VNC viewer dekstop is not Normale can any one tell me full commands for install VNC and fix normale dekstop view Thanks waiting

---

### Post by cbruce8 on 2011-08-08
sudo apt-get install tightvncserver ot 
sudo apt-get install vnc4server

in 'terminal'

---

### Post by arrrghhh on 2011-08-08
> **ManiKinG said:**
> hello need help,
 
i m trying to install VNC server on ubunto linux server via Putty ,
 
when i finish to install and login via VNC viewer dekstop is not Normale can any one tell me full commands for install VNC and fix normale dekstop view Thanks waiting

There is no "DE" or Desktop Environment (no point-and-click interface/GUI) included in the Server Edition of Ubuntu.

If you want a DE, I ***strongly*** recommend using the Desktop edition.  You can install/run all the same services on the Desktop edition.  Don't try to fit a square peg into a round hole by installing a DE on the Server edition...

---

### Post by ManiKinG on 2011-08-08
i did all this after login from vnc viewer i can see not gud desktop view have to install oh set gnome-session ?? how i can set ??

---

### Post by arrrghhh on 2011-08-08
> **ManiKinG said:**
> i did all this after login from vnc viewer i can see not gud desktop view have to install oh set gnome-session ?? how i can set ??

If you want a full DE, install Ubuntu Desktop.  Thanks.

---

