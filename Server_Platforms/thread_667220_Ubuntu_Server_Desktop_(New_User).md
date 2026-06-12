---
title: "Ubuntu Server Desktop? (New User)"
date: 2008-01-14
forum: Server Platforms
---

### Post by AStaley on 2008-01-14
I've just installed Ubuntu Server 7.10 to test for a new PostGreSQL server.  

The server keeps booting to a command prompt, how do I install the desktop, or get to the desktop?

I've downloaded the server edition from the Ubuntu website and when going through the install screens I couldn't see an option to include any desktop package.  Do I need install something like KDE seperatly?

I'm not only new to Ubuntu, but also Linux in gernal so this is a learning cure for me at the moment.

Thanks for any help, AStaley.

---

### Post by lintoolman on 2008-01-14
The following line is how to install KDE.

sudo aptitude update && sudo aptitude install kubuntu-desktop

---

### Post by Thanoulis on 2008-01-14
The Server Edition does not have X Window System installed...(generally a server does not need X)
I do not know if this works, but try to install ubuntu-desktop for Gnome or kubuntu-desktop for KDE, or xubuntu-desktop for XFCE.
```
sudo apt-get install ubuntu-desktop
```

If this doesn't work, try the desktop CD setup.

---

