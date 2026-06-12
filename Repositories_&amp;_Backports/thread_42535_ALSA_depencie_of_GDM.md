---
title: "ALSA depencie of GDM ?"
date: 2005-06-18
forum: Repositories &amp; Backports
---

### Post by Bramme on 2005-06-18
Hello,

I had to deinstall ALSA 1.0.8 to get my soundcard working with ALSA 1.0.9 (which is self-compiled)...
But ALSA is a depencie of GDM...
Why ?

And, are there any other display managers like GDM? (KDM is for KDE, XDM can not login automatically...)

---

### Post by diebels on 2005-06-18
Guess the best thing to do would be to make a deb package of the self-compiled alsa 1.0.9

You could make an init script with startx owned by your user and put "exec gnome-session" in /home/$USER/.xinitrck to log in automatically

---

