---
title: "New Web Server InstallationGUI or Command Line?"
date: 2010-04-16
forum: Server Platforms
---

### Post by M_Jewell on 2010-04-16
Newbie here, I am preparing to install 9.1 on what is to be a webserver and have been advised that a command line installation (no GUI) is  the preferred way to go. 
I guess I am wondering if this view is shared by all or if the GUI would be the better way to go? Any comment would be greatly appreciated.
MJ

---

### Post by cdenley on 2010-04-16
Having a GUI running is a waste of system resources, and provides an additional attack vector by which your system can be compromised. If you really feel like you need a GUI, though, just prevent it from starting at boot. Then, it will be there if you need it. I think with most server software, a GUI won't help much, though.

---

### Post by volkswagner on 2010-04-16
Gee, if one could search three character keywords on this forum, one could find the hundreds of posts on this topic....need a FAQ sticky?

Or perhaps search command line vs. Graphical user interface or desktop vs. server edition...not really!


Hmn, how would one query those hundreds of threads?

---

### Post by JonRohan on 2010-04-16
You could compromise and use web tools such as webmin on a headless server.

---

### Post by Iowan on 2010-04-16
[Here]("https://help.ubuntu.com/community/ServerGUI") is a help page...

---

### Post by jhollinger on 2010-04-16
Aye, a headless server is generally the way to go for both security and performance reasons. Now if it's just a hobby server sitting in your home LAN and isn't exposed to the Big Bad World, it might not matter so much. But even then I'd lean towards cli-only, as it will give you a nice sandbox in which to practice for that Big Bad World. And it will make you feel cooler.

Just so you aren't surprised, the Server Edition is bare bones. No, there aren't even bones; it's just bare. At the very least you'll want the command completion and man pages packages (apt-get install bash-completion man I think). You'll probably find others you thought were standard in every Linux OS, but those are the two biggies I always slap on.

---

