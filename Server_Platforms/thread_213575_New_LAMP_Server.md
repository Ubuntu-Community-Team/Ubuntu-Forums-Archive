---
title: "New LAMP Server"
date: 2006-07-11
forum: Server Platforms
---

### Post by jjr2527 on 2006-07-11
Ok, this will be a dumb question, as I type it I can already feel the sly remarks that will likely follow.  I installed the dapper LAMP default setup and then wanted to make some configuration changes like editing my network interfaces and repositories list.  However all of the examples of doing this use gedit which is not(apparently) included in the basic LAMP setup.  

I do want to install extras maybe even a desktop environment but the main purpose of the box will be as a web server.  Am I going about this the wrong way?

---

### Post by Kurt` on 2006-07-11
Your system has /usr/bin/vim and /usr/bin/nano (so just replace "gedit" with vim or nano in those examples, nano is probably less confusing though).

I actually did the same thing as you. :) I did a base server install, then later added GNOME, KDE, and XFCE to it for testing (apt-get install ubuntu-desktop, apt-get install kubuntu-desktop, apt-get install xubuntu-desktop). Sometimes I SSH into it, start GDM (Gnome's login manager), then VNC into it.

---

### Post by jjr2527 on 2006-07-11
Your response was swift, thorough, and (pending testing later at home) correct.

Thank you

---

### Post by az on 2006-07-11
> **jjr2527 said:**
>  However all of the examples of doing this use gedit which is not(apparently) included in the basic LAMP setup.  


I could find a guide to using the command line to manage your sources.list
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
But I could not find one for network configuration.

Any other guides that you find are missing?

---

