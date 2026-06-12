---
title: "Uninstall LAMP"
date: 2005-09-18
forum: Server Platforms
---

### Post by herrpoon on 2005-09-18
I've been having a few problems with PHP (not executing etc.) on my webserver, it was working at one point but not now, after searching these forums for help/solutions etc., I still haven't been able to sort it, so I think the best thing to do is to uninstall LAMP, I suppose I could just delete the concerning files but is there a better/more complete way of getting rid of LAMP, so I can reinstall it and start over?

---

### Post by herrpoon on 2005-09-18
I've found the command to uninstall it:
```
sudo apt-get remove --purge apache2
``` 

And did that for all the other stuff (PHP, mysql etc.) but all the files/directories are still there, so I'm reluctant to install over that as I don't want to completely screw it up.  Should I just delete all the files/folders?

---

### Post by LordHunter317 on 2005-09-18
Apt-get won't purge every package it removes, just the ones explictly specified on the command line.  If you want to purge (remove conffiles) for every package on your system, run this:```
dpkg --get-selections | grep deinstall$ | cut -f1 | xargs sudo dpkg --purge
``` I would leave off the xargs part first and view what will be removed before you run it, as you will not be prompted.  This may not remove every directory, but it will tell you what it doesn't remove, so you can kill it manually.

---

### Post by herrpoon on 2005-09-18
Ahh ok, many thanks, I managed to sort out my original problem in  the first place but that will come in handy if I need to make any more permanent changes.

---

