---
title: "what pakages are need to install gnome on server edition"
date: 2009-04-21
forum: Server Platforms
---

### Post by ugashia on 2009-04-21
I am undertaking a little project that will involve me installing Ubuntu 8.10 server edition on a HP ML115 G5 server, and I will need a GUI. But here is that catch, NO INTERNET. So I was wondering what packages I should download to have a up and running Gnome GUI or even a XFCE. Thanks for any help in advance ;)

---

### Post by BkkBonanza on 2009-04-21
Google: install gnome server, found this page, no waiting:
[http://ubuntuforums.org/archive/index.php/t-186298.html](http://ubuntuforums.org/archive/index.php/t-186298.html)

quick version:

sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg

All that should be available on the normal desktop cd but I don't know whats on the server cd.

---

