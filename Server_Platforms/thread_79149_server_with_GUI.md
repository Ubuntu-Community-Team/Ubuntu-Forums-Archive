---
title: "server with GUI"
date: 2005-10-19
forum: Server Platforms
---

### Post by hobbsifer on 2005-10-19
Hi, 
I've been running some linux desktops for a while now but still consider myself a relative newbie. For sure, I am a command line newbie. Most of my previous Linux desktop use has been heavinly augmented by GUI's. I need to setup a server for personal use and have a machine which I'd like to use as a server and workstation (rarely) combo. I used the Ubuntu 5.10 server i386 install disk, but after setup I could not get any GUI loaded (I did use the sudo install command to install xwindows, but couldn't launch it..). 

I would like to use the GUI for server config and also to run Gimp occasionally.

My question(s):
1. For my purposes, that is to have a server with a GUI, is it easier to go with a desktop installation and add server packages? 

2. Is there a way to install Gnome desktop on the BB 5.10 server default installation? 

TIA for any suggestions/feedback.

JH

---

### Post by Erin on 2005-10-19
Having a server sans GUI is more a production environ necessity. For a domestic machine. Regarding Q1, it depends on what you need for the desktop. Try a custom install, get X and the server apps you need installed at install time. 

As for your current problem, what error messages did you get trying to start X? If you've installed it, have you configured it?

Erin

---

### Post by hobbsifer on 2005-10-19
Thanks for your quick response Erin. I appreciate your suggestion for a custom install. Without sounding too clueless, would I type "custom" at the command prompt when doing a fresh install? 

I do not recall the error message after I attempted to install xwindows, but it was something like "not installed". Since my first post I have wiped the HD and am ready for a new install, perhaps your custom install would be best. I have another old machine which I did a default desktop install, and WOW it installs a lot of apps... 

JH

---

### Post by hobbsifer on 2005-10-19
N/M my below quesiton- I just found the instructions for a custom installation. Thanks again!

JH

[QUOTE=hobbsifer]Thanks for your quick response Erin. I appreciate your suggestion for a custom install. Without sounding too clueless, would I type "custom" at the command prompt when doing a fresh install? 

I do not recall the error message after I attempted to install xwindows, but it was something like "not installed". Since my first post I have wiped the HD and am ready for a new install, perhaps your custom install would be best. I have another old machine which I did a default desktop install, and WOW it installs a lot of apps... 

JH[/QUOTE]

---

### Post by Beernut on 2005-10-19
You can do a server install and then install Webmin. 

"web-based administration toolkit
Webmin is a web-based interface for system administration for Unix. Using
any browser that supports tables and forms (and Java for the File Manager
and telnet/ssh modules), you can setup user accounts, Apache, DNS, file
sharing and so on."

---

### Post by Velox Letum on 2005-10-19
Even on my production desktop box I run Webmin, it makes it easy to administrate many tools that otherwise are run from the command line.

---

