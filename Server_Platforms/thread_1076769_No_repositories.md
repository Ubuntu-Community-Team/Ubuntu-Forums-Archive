---
title: "No repositories?"
date: 2009-02-21
forum: Server Platforms
---

### Post by Legolas8911 on 2009-02-21
I'm having troubles installing GUI on server edition.when i enter apt-get install xinit it says that cannot find a package candidate or something like that.the same with Midnight Commander.in aptitude -u,it gives me a list with different sites starting with ro.ubuntu.com(i guess).some of them are green and it says [IGNORED]
 and some are red with [No such file,or something like that] label.what can i do?

---

### Post by R.Bucky on 2009-02-21
Wouldn't you want to install ubuntu-desktop or kubuntu-desktop instead of xinit?

---

### Post by Legolas8911 on 2009-02-22
with ubuntu-desktop or kubuntu-desktop it says "No package found" or something like that :(

---

### Post by E_K on 2009-02-22
nano /etc/apt/sources.list

then uncomment every comment except for the cd at the top, leave/comment that one out

apt-get update
apt-get install [whatever you want]

if you get permission errors, use su or sudo the command

:)

Still not working, find a good copy of sources.list from google for your distro

---

### Post by Legolas8911 on 2009-02-22
It's working after a aptitude -update.I have installed GUI and various other things.Thanks for helping guys :popcorn:

---

### Post by E_K on 2009-02-22
no worries glad its working :)

---

