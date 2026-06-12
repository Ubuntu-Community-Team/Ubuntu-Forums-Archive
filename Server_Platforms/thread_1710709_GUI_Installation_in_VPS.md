---
title: "GUI Installation in VPS"
date: 2011-03-20
forum: Server Platforms
---

### Post by thunderclap on 2011-03-20
I know I can install the GUI of Ubuntu on a VPS and connect to it, but I'm curious if I install this if it will affect my live server? Will any of my configuration settings be changed rendering connection to my site impossible? Is there are easy way to back the site up (OS, configuration files, etc.) that can be restored if something goes wrong?

Any help is appreciated.

---

### Post by stmiller on 2011-03-20
backups are a unique and 'hot' topic. There is no one way. :/

If your VPS provider offers backups, that's obviously a good choice.

Otherwise options include making a tar ball ('zip') of the entire /etc/ directory which has pretty much all config files.

If you use mysql, it is possible to make a dump of the entire database as a backup. (mysqldump command)

But anyways I'd suggest checking out webmin -> [http://www.webmin.com/](http://www.webmin.com/)

It's a web interface for managing a Linux server. Then you don't have to have the gnome desktop, etc. but just remotely make changes from your browser.

---

