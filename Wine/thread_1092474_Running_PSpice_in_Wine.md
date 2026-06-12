---
title: "Running PSpice in Wine"
date: 2009-03-10
forum: Wine
---

### Post by klisc on 2009-03-10
I tried running PSpice in wine, and It didnt work. I couldn't place parts. So then I tried reinstalling PSpice on wine, with no success. So then I tried to reinstall wine. When I uninstalled wine, the folder containing the PSpice programs was still on the main menu. Then I reinstalled Wine. I deleted the .wine folder, and tried reinstalling pspice, and it did not work, It allowed me to go through all of the menus but when I got to the part with the progress bar, the installed would just close. Is there a way to fix this or work around it? (preferably both issues)
 Thanks for the help

---

### Post by cogadh on 2009-03-10
PSpice has spotty performance at best in Wine, but you may find some helpful info here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1026](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1026)

---

### Post by orethrius on 2009-03-10
cogadh beat me to it.  Regardless, this appears to be a known issue.  Wine has decent support for several programs, but - as it's still a partial reimplementation of the Windows APIs - it does not currently cover everything.  Here are a couple links that may be helpful in solving this problem.

Possible Workaround: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1026](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1026) (scroll down)
Bug Report: [http://bugs.winehq.org/show_bug.cgi?id=3023](http://bugs.winehq.org/show_bug.cgi?id=3023)

---

