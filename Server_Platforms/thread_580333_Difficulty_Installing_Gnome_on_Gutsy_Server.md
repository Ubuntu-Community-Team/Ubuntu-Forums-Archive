---
title: "Difficulty Installing Gnome on Gutsy Server"
date: 2007-10-18
forum: Server Platforms
---

### Post by atrdallas on 2007-10-18
I installed Gutsy Server 7.10 today from scratch on a previously working 7.04 box.  However, aptitude and apt-get will not install Gnome due to broken dependences.  I have added the Gutsy Desktop 7.10 CD-ROM to the apt source list.  I am surprised that neither CD contains the necessary Gnome packages.  What am I doing wrong?

---

### Post by dmizer on 2007-10-18
okay, maybe i'm missing something ... but why did you install ubuntu server if you wanted gnome?

if you want full gnome, just install with the regular ubuntu cd, or the alternate cd, then update with your desired server apps.

or in other words, even if it doesn't say "server" on the cover, you can still use it as a server.  however, if it says "server" on the cover, it's probably not a good idea to try using it as a desktop (install gnome).

---

### Post by twistedtwig on 2007-10-19
I would guess they would like the pre configuration of the gusty server install but with a GUI

---

### Post by atrdallas on 2007-10-19
I double checked the apt config file and found that one of the web sources was commented out.  Uncommenting that line allowed Gnome to install properly.  As to why I wanted Gnome on a server, I occasionally need to use Firefox locally to test websites.  This is a demo server.

---

### Post by dmizer on 2007-10-19
notice i didn't ask why you wanted to install gnome.  that's your business.

just odd that you should want to install it after having installed a server.

here's why.

gnome is a meta package with hundreds (ok, not "hundreds", but a lot) of programs to install, each which could cause problems or mess with your server functionality, or cause problems with hardware operation.  nothing seems to have gone wrong for you. but why risk it when updating a normal gnome ubuntu install with your server applications only requires installing a few programs.  for example:
```
sudo aptitude install apache2
```
is all that's needed to install a pre-configured/ready to go webserver on gnome.

---

