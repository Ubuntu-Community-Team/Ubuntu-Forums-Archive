---
title: "Mounting iPod Touch"
date: 2011-01-26
forum: Wine
---

### Post by Sailor5 on 2011-01-26
Greetings!

So I'm in need of a restore for my iPod Touch. However of course I want to do it from my native OS, Ubuntu. I've installed iTunes with the latest version of Wine. Now however I'm needing to mount the iTouch with Wine. Where is it mounted under though? In the '/media/' folder?

Thanks bye!

---

### Post by johntaylor1887 on 2011-01-27
I'm having the same problem. I had to resort to using windows to restore mine in itunes proper. It would be nice if I could do it in ubuntu, but I'm going to keep looking for answers.

My best guess is that the latest updates for itunes/ipods is keeping them from playing nice with linux.

---

### Post by johntaylor1887 on 2011-01-27
I found a solution to get my it mounted and recognized by ubuntu. I added [this]("https://launchpad.net/~pmcenery/+archive/ppa") PPA to my sources list and installed ifuse 1.1.1 

Rhythmbox now sees it, but I don't know if iTunes via wine will. You may need a windows machine to restore it.

---

