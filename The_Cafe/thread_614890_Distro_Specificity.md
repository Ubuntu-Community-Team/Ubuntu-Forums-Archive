---
title: "Distro Specificity"
date: 2007-11-16
forum: The Cafe
---

### Post by Tlon on 2007-11-16
I've run into a rather annoying problem at work.  We're mostly a Wintel shop, but myself and a few others have managed to justify a few Linux boxes.  Me and everyone else comes from a Debian background, so naturally we'd prefer to use Ubuntu.  The problem I've run into is that a lot of the apps seem to demand Fedora or RHEL, without giving any particular reason as to why.  One example is Websense (the admin client).  I try to install it, only to be presented with an error message, "Your operating system is not compatible."  It's not the operating system but the distro; the documentation says that it's only compatible with Redhat flavors.  What I want to know is why that would be.  If it's just the minor differences in directory structure, then one would hope that they wouldn't hard-code such a thing (config files, anyone?).  Otherwise, you'd think that the problem would be restricted to having the proper libraries installed, e.g., GTK or QT.

Anyone else had to deal with this?

---

### Post by blueturtl on 2007-11-16
Well technically Red Hat and Ubuntu and Debian are different operating systems. They are simply based on the same kernel. This idea that all the same things work on all flavors of Linux-kernel based operating systems is both a blessing and a curse.

Similarity allows for easy porting of features and applications, but on the other hand it kind of stops any of the operating systems from clearly differentiating. I've run into a lot of resentment from users of other Linux based operating systems that has to do with Ubuntu not having a root account. They automatically expect Ubuntu to work like the other operating systems they are used to.

If I were to develop an app spesifically for Ubuntu it probably would not run on Red Hat without some tweaks because of the internal differences. Because of the same heritage of the operating systems it probably would not require much to make it work though. For the same reason it is probably easier to port apps from the Mac OS to Linux than say from Windows to Linux.

If you expect support for an application on a system it was not intended for you're probably going to have to do the work yourself or hope that enough people from your operating system's community are interested so that a maintainer for a new port could be found.

---

### Post by Frak on 2007-11-16
Since most large servers run either RHEL, SLED, or WS(C), I can see the reason for Websense only wanting RPM based distributions. There is a way to bypass this (via lsb), but I can't quite think of it ATM.

We use websense where I work, I administer it. Bad peice of software IMO.

---

