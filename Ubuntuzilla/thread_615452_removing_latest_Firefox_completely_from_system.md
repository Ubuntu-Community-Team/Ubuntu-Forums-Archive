---
title: "removing latest Firefox completely from system"
date: 2007-11-17
forum: Ubuntuzilla
---

### Post by dynamethod on 2007-11-17
Hey there, i was running the repo version of FF, I downloaded ubuntuzilla to update to the latest version of firefox, but the lastest version is butt ugly, the tabs are out of shape etc etc, so i tried removing FF for a clean install, i got the repo version removed, but i have no idea how to remove the latest version that ubuntuzilla installed (2.0.0.9), ive looked through [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/) and cant seem to find the entry where it tells you how to remove the dl update from your system, only how to remove ubuntuzilla itself, help much appreciated

---

### Post by dynamethod on 2007-11-17
....just found where ubuntuzilla dl and installed the latest firefox to... /opt - why?

How do i go about removing it COMPLETELY from my system?

---

### Post by lakris61 on 2007-11-17
This could do it:
> lakris@ubuntu:~$ which firefox
/usr/bin/firefox
lakris@ubuntu:~$ file /usr/bin/firefox
/usr/bin/firefox: symbolic link to `/opt/firefox/firefox'
lakris@ubuntu:~$ sudo rm /usr/bin/firefox
lakris@ubuntu:~$ sudo rm -rf /opt/firefox

Run which firefox again to see if there may be other links to it.  The point is to find which firefox gets started and remove links to it and its directory. I don't think it puts files anywhere else than in its own directory and a symlink somewhere in the path.

/Lakris

---

### Post by nanotube on 2007-11-17
hi, apparently you didn't read the ubuntuzilla instructions carefully enough. :)
to remove ubuntuzilla's version of firefox, run
```
ubuntuzilla.py -a remove -p firefox
```
:)

---

