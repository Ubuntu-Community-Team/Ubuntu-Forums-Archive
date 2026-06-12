---
title: "Switching to Server"
date: 2008-04-22
forum: Server Platforms
---

### Post by calelettus on 2008-04-22
Pardon if this isn't the correct forum but I am running 7.10 desktop on a newly built pc that I have decided to use as a home media 

Would it be better to wipe and reload Ubuntu Server - starting completely new - or can I just remove unnecessary packages from the desktop install and if so, how exactly should I do it? 

I would be accessing the box remotely using Ubuntu desktop. Thanks!

---

### Post by mrsteveman1 on 2008-04-22
I would just leave desktop on

Server is really intended for web services, headless rack servers etc. You would have to install X11 and a desktop on Server, and by that time you could have just used desktop anyway, because it would be almost identical but for the kernel.

I'm not even sure whats different in the kernel anyway.

---

### Post by craylim on 2008-04-22
if it's for home use, leave the desktop install as it is and apt-get new packages you may need to provide the services you want.  You'll probably want to use it for web-surfing and other works as well so the GUI will be handy.

Server install does not install GUI by default.  For me, it is for my servers in the datacenter where I normally only ssh in for configuration and maintenance in CLI.

---

