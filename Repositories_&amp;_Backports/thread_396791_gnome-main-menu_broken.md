---
title: "gnome-main-menu broken?"
date: 2007-03-29
forum: Repositories &amp; Backports
---

### Post by Screevo on 2007-03-29
I'm attempting to install the gnome-main-menu package via apt-get install gnome-main-menu.

It throws up an error that libdbus is not present, or possible a broken package. Since LibDBUS is installed (and in a newer version than required), I can only conclude the package is broken.
```

stephen@screevo-z81ka:~$ sudo apt-get install gnome-main-menu
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-main-menu: Depends: libdbus-1-2 (>= 0.60) but it is not installable
E: Broken packages
stephen@screevo-z81ka:~$ sudo locate libdbus
/var/cache/apt/archives/libdbus-1-3_0.93-0ubuntu3.1_i386.deb

```

---

### Post by silverglade00 on 2007-04-01
That looks to me like your locate found the .deb for libdbus, not the installed libdbus itself. Try running 

sudo dpkg -i /var/cache/apt/archives/libdbus-1-3_0.93-0ubuntu3.1_i386.deb

then

sudo apt-get install gnome-main-menu

It looks like for some reason it downloaded libdbus as a dependency, but didn't think to install it for you. :)

---

