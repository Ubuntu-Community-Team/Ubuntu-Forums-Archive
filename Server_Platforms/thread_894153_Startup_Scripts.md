---
title: "Startup Scripts"
date: 2008-08-19
forum: Server Platforms
---

### Post by neutrino15 on 2008-08-19
This is probably a very basic question, but how would I go about launching a program on system boot? My ubuntu server is headless and does not run X or Gnome at all, so I can not use the GUI that your documentation suggests.
I am very new to linux, but I essentially want the box to do things like launch ddclient daemon, launch rtorrent, launch apache, etc.. without any human intervention.

Thanks for your help!

---

### Post by neutrino15 on 2008-08-19
Nevermind, I found an article via google:

[http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

---

### Post by MJN on 2008-08-19
You may prefer (find it easier) to launch one-shot applications at startup by adding them to /etc/rc.local - this script gets parsed every boot following the completion of the runlevel.
 
Note that many applications will already be configured to run at boot - e.g. Apache and, presumably, ddclient from your list.
 
Mathew

---

