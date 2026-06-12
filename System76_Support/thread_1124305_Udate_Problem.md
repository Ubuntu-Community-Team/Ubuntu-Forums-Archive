---
title: "Udate Problem"
date: 2009-04-13
forum: System76 Support
---

### Post by MarkID on 2009-04-13
I was trying to install upgrades and I got this message.  What does it mean?  What do I do?  Please make your answer as specific as possible.  Thank you.


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


System:  PanP4n, Intrepid.

---

### Post by drs305 on 2009-04-13
```
sudo dpkg --configure -a
```
You must run it as root. Enter that command in a terminal. It will ask for a password. Type your password - you won't see it being entered for security reasons. Hit ENTER once you have typed it in.

You can read what the switches do with the dpkg command by reviewing the *man* page: in a terminal type "man dpkg".

---

