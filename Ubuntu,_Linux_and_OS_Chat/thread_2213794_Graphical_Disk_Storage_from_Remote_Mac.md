---
title: "Graphical Disk Storage from Remote Mac"
date: 2014-03-28
forum: Ubuntu, Linux and OS Chat
---

### Post by jingo_man on 2014-03-28
the main partition with the system installation is running out of space. this is a Ubuntu server (headless) install.

my main daily computer is a Mac. is there a binary / daemon i can use to produce a dynamic (preferred) or at least static graphical treemap representation of the used space that i can view from the Mac? My presumption here is most would use a browser based interface, but I have no problem is any Mac app / binary exists that I can select remote Ubuntu servers to scan / display from.

i have seen baobab (disk utiliser) but this seems entirely Ubuntu centric, which is no use to me. i have also installed webmon and monitorix on this server too, so if there are means to use these, that would also be fine.

hope for some good suggestions...

---

### Post by bapoumba on 2014-03-29
How do you usually connect to the server ?
From the MacOS X Finder : command-K ?

---

### Post by jingo_man on 2014-03-30
I typically connect via SSH for most admin tasks, etc.

However I have also configured numerous apps, etc, on this box too. Most run through browser-based use, i.e. webmin, monitorix, among others.

I can also see the server's SMB Shares in the Mac's Finder. I could also connect through your indicated method above too.

None of these are able to provide the same form of output regarding disk usage that the Disk Usage Analyzer / Boabob apps do which is what I require, I would just like the main binary to run from the Mac and remotely connect into the Ubuntu.

---

### Post by bapoumba on 2014-03-30
Looking around it appears that baobab is available on macports (should bring some gnome packages as a dependencies).

[https://www.macports.org/ports.php?by=category&substr=gnome](https://www.macports.org/ports.php?by=category&substr=gnome)
[https://www.macports.org/](https://www.macports.org/)

Edit: Moved to Other OS Chat.

---

