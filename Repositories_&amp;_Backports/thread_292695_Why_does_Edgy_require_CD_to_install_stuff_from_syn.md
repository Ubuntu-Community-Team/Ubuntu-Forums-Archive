---
title: "Why does Edgy require CD to install stuff from synaptic/apt"
date: 2006-11-04
forum: Repositories &amp; Backports
---

### Post by navneeth on 2006-11-04
Till now I've wanted to install only a couple of things, but both times I was asked to insert the CD before installing. Both Synaptic and apt-get does this. This didn't happen in Dapper. Any ideas why this is happening? :confused:

---

### Post by aysiu on 2006-11-04
You probably have the CD repository listed in your sources.list.

```
sudo nano -B /etc/apt/sources.list
``` Comment out the line with the CD-ROM in it.

Uncommented: ```
deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
```

Commented out: ```
#deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
```

---

### Post by wjp.reg on 2006-11-04
Have you checked that all repositories are checked and available to synaptic? Not in front of my ubuntu system right now, but one of the menu items let's you maintain these.  Otherwise open a terminal and check /etc/apt/sources.list to see if any repos are commented out with "#".

What you described has happened to me before too.

---

### Post by navneeth on 2006-11-04
Hey, Asiyu! Thanks! Now apt-get doesn't ask me to install the CD. :) Btw, there were two lines, and both were

```
 cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
``` 

excpet that one was commented and the other was not. I commented the one that was not. 

wjp.reg,
     I have not checked the repositories. I'm trying to open Synaptic but it tells me that there is something else running (apt-get or aptitude) and wouldn't open ("Unable to get exclusive lock"). I've even closed the terminal. 

Could someone tell me how to "exit" apt-get after an aborted download?

Thanks.

---

### Post by aysiu on 2006-11-04
Try: ```
sudo apt-get -f install
```

---

