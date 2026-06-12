---
title: "Light KDE or Gnome for Ubuntu Server"
date: 2010-02-16
forum: Server Platforms
---

### Post by ortuno2k on 2010-02-16
Hello,

I'm quite new to Ubuntu and the whole Linux world. I have managed to install and configure a home-based file server with Ubuntu 9.10 Server edition. At first, the lack of GUI was somewhat shocking, but I've become used to it.
Trying out other Linux distros, (CentOS, Fedora), I've noticed that they DO have a GUI; one that feels light and just "right."
I've tried to install Gnome-Desktop on top of Ubuntu server, but that makes a huge mess. I don't want all those "desktop" apps and utils that I'll never use.

What I'm looking for is a very, very plain GUI-like version of KDE or Gnome, with a file browser (Nautilus?). Something like that...

Is there such a thing out there? If not, how can I make my own? I've yet to experiment to do any Linux programming or building my own kernel, but I'm not afraid to do so.

I have some knowledge of C, C++, Python...if that helps.

Thanks!

---

### Post by ortuno2k on 2010-02-17
Dang nobody can add something to say to this?
Are we all Linux noobs coming here looking for answers?

---

### Post by wojox on 2010-02-17
Pretty minimal:

```
sudo apt-get install 
gdm xorg gnome-core gnome-codec-install 
indicator-session-applet update-manager 
firefox-3.5-gnome-support gnome-themes 
network-manager gdebi
```

---

### Post by ortuno2k on 2010-02-17
Thank You Wojox! This is exactly what I needed!!!

---

