---
title: "Do server and desktop have different repos?"
date: 2009-03-08
forum: Server Platforms
---

### Post by kthxbai2u on 2009-03-08
I am trying to figure out why gdm crashes... I just remembered I copied a sources.list from an 8.10 desktop and put it on the 8.10 server.

Would this cause gdm to fail because there are 2 seperate repos or is there only one?

---

### Post by mrsteveman1 on 2009-03-08
Nope, there isn't any real difference. There is a different kernel package for specific reasons outlined on the Ubuntu frontpage, but otherwise the sole difference is that ubuntu-desktop and ubuntu server have a different metapackage controlling what gets installed.

Every machine i have has the repos set to these:

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-security main restricted universe multiverse

---

### Post by kthxbai2u on 2009-03-08
you wouldn't happen to know how to force 640x480 resolution in 8.10 would you? it cannot be done via xorg.conf for some reason... I only have console / shell access.

---

### Post by mrsteveman1 on 2009-03-08
Make a new thread about the screen thing so it can be easily found in a search by someone looking for help etc. It should just do what you tell it to do in xorg.conf.......

You could also try dpkg-reconfigure xserver-xorg

---

