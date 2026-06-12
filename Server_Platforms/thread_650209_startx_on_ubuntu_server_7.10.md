---
title: "startx on ubuntu server 7.10"
date: 2007-12-26
forum: Server Platforms
---

### Post by lthuong on 2007-12-26
How to install startx service on Ubuntu server to run program from GUI. Thanks.

---

### Post by HermanAB on 2007-12-26
Install Gnome, KDE or Xfce (Xfce is best for a server).  The desktop system will cause Xorg to be installed as a dependency.

Cheers,

H.

---

### Post by kerry_s on 2007-12-26
servers don't have a gui. you can install 1.
example:
sudo apt-get update
sudo apt-get install xorg (what ever WM or DE you want)
startx

the 3 main DE's are gnome, kde, xfce4
there is also several WM's if you don't need a whole desktop environment.

for a server you only want to install what you need. for example, say you want to do things with a file manager, you can just install " mc " (sudo apt-get install mc) " man mc " to read the manual
you don't need a DE or WM and it still makes things easy. for a server the more things you install, the more things might have weaknesses to exploit.

---

