---
title: "Autologin and execute 'screen /dev/ttyS0 ...'"
date: 2010-05-12
forum: Server Platforms
---

### Post by KamakazieX on 2010-05-12
[CENTER][/CENTER]I have installed ubuntu server to an older P3 laptop to be used as an appliance / console port for an older Alpha box that does not support regular monitors for some reason. I would like to create a user 'console' to auto login after boot and execute ```
screen /dev/ttyS0 9600 vt100
``` and 'poweroff' after the console session is exited. I would like to do it this way so if it needs to be used for any other purpose I can switch alt+fn and logon as a superuser for other purposes.

Any help with this?

Recommend another comm's app?

---

### Post by Bachstelze on 2010-05-12
> **KamakazieX said:**
> I would like to create a user 'console' to auto login after boot and execute ```
screen /dev/ttyS0 9600 vt100
``` and 'poweroff' after the console session is exited.

AFAIK, a regular text-only Linux will not allow a user to autologin. You will have to install X with a display manager like GDM (which will take care of the autologin) and maybe a lightweight window manager like Fluxbox. Then you can use your X session to automatically fire up a xterm with your comm program running in it at login.

> **KamakazieX said:**
> Recommend another comm's app?

Minicom is nice, it's what I use to control my Soekris boxes when SSH is down for some reason or another.

---

### Post by KamakazieX on 2010-05-13
How about an autoexec to run the terminal emulator at an rc level so it executes in the userspace w/o logging in?

---

