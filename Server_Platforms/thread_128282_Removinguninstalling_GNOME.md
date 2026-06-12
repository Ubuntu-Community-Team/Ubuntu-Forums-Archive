---
title: "Removing/uninstalling GNOME"
date: 2006-02-11
forum: Server Platforms
---

### Post by Pugi! on 2006-02-11
Yesterday I installed Ubuntu server ... works for the moment, not quite finished yet. But I am still bit of newbie so I thought it would be helpful if I had a GUI instead of only commandline. I installed GNOME with apt-get. Startx doesn't work, get some errors. When I reboot it starts GNOME, I don't want that - I only want to use GNOME when I choose to do so, and fails;  a lot of bright colors and I eventually end up in commandline.

How do I remove or uninstall GNOME ? So I can at least have clean system that boots commandline. How do I install gnome, kde or whatever correctly so that I can use a GUI when I want to ?

thanx,

Pugi!:confused:

---

### Post by aysiu on 2006-02-11
Have you tried ```
sudo apt-get remove xserver-xorg-core
```?

---

### Post by bastya_elvtars on 2006-02-11
[http://www.ubuntuforums.org/showthread.php?t=80423&page=3](http://www.ubuntuforums.org/showthread.php?t=80423&page=3)

Use remove instead of add at gdm. :)

---

