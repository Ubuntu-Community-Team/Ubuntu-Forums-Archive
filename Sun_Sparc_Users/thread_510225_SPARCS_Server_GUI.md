---
title: "SPARCS Server GUI"
date: 2007-07-26
forum: Sun Sparc Users
---

### Post by Amisten on 2007-07-26
Hello everyone, you will have to excuse me because I'm somewhat new to linux and such. I'm sitting here with a Sunblade 150 and just for shits and giggles I want to load a GUI interface onto it. Now, I've noticed that with ubuntu, the only thing available is a text based server edition which is not really what I'm looking for. Actually I'm not even looking for a server, just a GUI of lunix I can load onto it. So, I have looked all through the ubuntu forums here and tried to load the desktop ubuntu thru the server but it never seems to go. Says something about not being able to find the packets. Point is, I was wondering if anyone here could either help me fix this problem or maybe point me in the direction of a linux distro that supported SPARCS on their desktop version.

Thank you so much for your help.

---

### Post by ErusGuleilmus on 2007-07-26
If you are just wanting to use it as a computer and not a server, use the Desktop edition instead of the server edition.

---

### Post by Amisten on 2007-07-26
Well I would if I could find one. When you select the desktop edition with SPARCS processor it downloads the server edition still. It leads me to believe that there is no desktop edition for the SPARCS processor. If I'm wrong could someone post a link cause it seems I can't get to it, at least with ubuntu.

---

### Post by netztier on 2007-07-26
> **Amisten said:**
> Well I would if I could find one. When you select the desktop edition with SPARCS processor it downloads the server edition still. It leads me to believe that there is no desktop edition for the SPARCS processor. If I'm wrong could someone post a link cause it seems I can't get to it, at least with ubuntu.

Just install the meta-package **ubuntu-desktop** (or kubuntu-desktop or xubuntu-desktop, for that matter).

But a word of warning: There's  issues with the desktop packages for SPARC - running X.org with these packages can become daunting. Some ATI based graphics cards just plain refuse to run - others work from the start. Permedia-based chips with the glint driver are very tricky, too. All X servers are unaccelerated and can't profit from the graphics chips capabilities - so keep your expectations low.

Other issues arise with HAL - it's not working well at the moment, and it leaves Gnome-Desktop in a state where you can't properly work with it. The *buntu-desktop from Ubuntu 6.06 LTS's are better in that regard, as long as you don't run OpenGL - something seems broken with the Mesa libraries and X.org crashes instantly.

What you could do, is run **remote-X**; install a desktop package on the server, and configure it for to allow XDMCP logins from the network. You should then be able to login remotely from your workstation, maybe even in a nested X window from your desktop. This puts some load on the network (not recommended via WAN/Internet), but leverages the CPU load on the Sun considerably, since it doesn't have to do the graphics calulations itself.

But for the rest - well go ahead!

best regards

Marc

---

### Post by Amisten on 2007-07-27
Thank you for your help. It seems I'm not too sure how to install this meta package. Is it something that is in the installation on my HD, on the CD or downloadable for that matter?

Maybe there is a better choice for what I'm looking to do. Is there a distro that supports SPARCS with a GUI to begin with? Its a shame that I wouldn't be able to have ubuntu on there but I'm just toying to begin with. We got this thing( Sunblade 150) at work with Solaris on it, no password and no documentation, so I'm just trying to make it functional.

Again Thanks for your help.

---

### Post by netztier on 2007-07-27
> **Amisten said:**
> Thank you for your help. It seems I'm not too sure how to install this meta package. Is it something that is in the installation on my HD, on the CD or downloadable for that matter?


Eh - then you should get used to **apt**, the package management system that Debian Linux uses - and since it's Debian-based itself, is also used by Ubuntu. It comes preinstalled, as it is the most recommended software installation/removal tool for debian-based distributions.

In a nutshell: Ubuntu has a wealth of software in it's repositories, of which you'll only find the bare basics on a CD. Yet, there's an entire Universe, nay... a *Multiverse* of applications available for Ubuntu (pun intended... you'll understand it once you've read about "Softare repositories"), all via Internet. Using software from these sources is the standard way to add/remove software from an Ubuntu installation. 

You *could* always go the hardcore way and compile everything yourself or download non-,deb software packages from non-ubuntu-sources. But soon you will discover that with the things you get from the Ubuntu repositories, everything neatly fits together, and that this makes **apt** so great.

Software packages come as .deb files, and these can come from almost anywhere; the **apt** system can use CDs, Harddisks, http servers, ftp servers... etc. Most often, you'll be using an internet-reachable source that is contacted via http. The configuration file **/etc/apt/sources.list** holds a predefined set of software repositories for you. 

**apt** uses the **aptitude** or **apt-get** command line programs or **synaptic** as frontent when running a GUI.

You might want to start reading and exploring here

[https://help.ubuntu.com/](https://help.ubuntu.com/) (second chapter)

and more specific on apt:

[https://help.ubuntu.com/7.04/add-applications/C/advanced.html#apt](https://help.ubuntu.com/7.04/add-applications/C/advanced.html#apt)


best regards

Marc



PS: since a Desktop environment consists in itself of hundreds of .deb packages, so-called meta-packages like "ubuntu-desktop" (which you can find with "sudo aptitude search ubuntu-desktop") are just listings of which packages to (download and) install.

---

