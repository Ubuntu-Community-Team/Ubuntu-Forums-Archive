---
title: "Circunvent the administration directory lock when installing different things"
date: 2008-01-11
forum: Ubuntu Brainstorm
---

### Post by inoxllor on 2008-01-11
Background:
========

If we are running an UPDATE/INSTALL via apt-get or synaptics we cannot install a package and vice-versa. 

All we get is something like this:
[HTML]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/HTML]

In Windows we can cheat the installation process and install 2 or more programs at the same time.

Possible Solution:
===========
How about implementing something like an **automatic installer task scheduler**.

Per example.: if I run *apt-get install gnome-desktop*, the installer starts, so if then I run in another terminal session *apt-get install kde-desktop* it automatically schedules it as the next task to do and so on.

In this way I can browse the internet or play a game and the computer handles all the installation tasks for that session.

What do you think?

---

### Post by maybeway36 on 2008-01-11
If this is to be implemented, we should work together with Debian on this.

---

### Post by lexen on 2008-01-14
I have run into many times when I wanted to install two programs at once, but I understand that it would mess things up.  If you want to install one program and then another without you having to do anything in between, you should just use synaptic.  If you still want to use command prompt then you could type:

sudo apt-get install gnome-desktop kde-desktop

If you simply put a space between the names of the programs, it will download them and install them when the download is done.  This works for as many programs as you want to install, not just two.

The only time I can think of where you will run into problems is where you forget that you wanted something and the install of the first program will take a long time.  It happens, but I don't think it's worth tailoring the OS for that situation.

---

### Post by maybeway36 on 2008-01-14
There is no kde-desktop packge in Ubuntu :P

---

