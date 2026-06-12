---
title: "Install packages"
date: 2014-11-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Peter_R._Larsen on 2014-11-07
Is it possible install packages from cd/dvd iso's, like copy the file let say from Linux Mints vlc package ( i got bored, trying something may not be possible)

Booting from Debian 7.7.0 and insert Linx Mint 17 Cinnamon dvd or from ubuntustudio and copy some packages and Install them?

---

### Post by TheFu on 2014-11-07
You **can** install .deb files, provided the mandatory dependencies are met
**HOWEVER** - and this is big - **that is a terrible idea**.  It will probably break system dependencies at some point and make the system be unpatchable.  This isn't Windows. There are lots of moving parts, provided by hundreds of different teams around the world. Those dependencies can be shallow or deep. The deeper they are into the core OS, the more likely installing a package manually from a .deb file will lead to a problem.

Until you understand that stuff completely, best not to do it on a system you want to maintain longer than 6 months or so.

---

### Post by Peter_R._Larsen on 2014-11-07
> **TheFu said:**
> You **can** install .deb files, provided the mandatory dependencies are met
**HOWEVER** - and this is big - **that is a terrible idea**.  It will probably break system dependencies at some point and make the system be unpatchable.  This isn't Windows. There are lots of moving parts, provided by hundreds of different teams around the world. Those dependencies can be shallow or deep. The deeper they are into the core OS, the more likely installing a package manually from a .deb file will lead to a problem.

Until you understand that stuff completely, best not to do it on a system you want to maintain longer than 6 months or so.

thank you that was very helpful

---

### Post by grahammechanical on 2014-11-07
We can use a live session/install DVD as an offline repository. We can even create our own offline repository. 

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

Regards.

---

### Post by buzzingrobot on 2014-11-08
> **Peter_R._Larsen said:**
> Is it possible install packages from cd/dvd iso's, like copy the file let say from Linux Mints

The overwhelming majority of Ubuntu packages are migrated over from Debian.  Even more of Mint is built directly on Ubuntu packages. Applications available in one of those distributions are almost always available for installation in the usual way in the others, although the specific versions can vary from release to release.

Installing a package is seldom a matter of just copying a single file. Applications usually contain any number of files, and the packages that we use to install them include data and scripts to make sure all the pieces end up in the right spots in the filesystem.   Any other packages -- the dependencies -- needed will be downloaded and installed *if we use* programs created to do that, like the Software Center, apt, Synaptic, etc. 

Debian packages can be searched at packages.debian.org.  Ubuntu packages can be searched at packages.ubuntu.com.  Both show a package's dependencies, changelog, etc.

Mint packages are at packages.linuxmint.com.  Since Mint relies on Ubuntu repos, there are relatively few packages there, so they're browsable instead of searchable.

[EDIT:  But, yes, technically, packages can be downloaded and installed locally using Software Center, apt, etc. That should work using an Ubuntu package on Ubuntu, a Mint package on Mint, etc.  Trying to install a foreign package is risky for a number of reasons.]

---

### Post by Peter_R._Larsen on 2014-11-08
> **grahammechanical said:**
> We can use a live session/install DVD as an offline repository. We can even create our own offline repository. 

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

Regards.

Using Debian 7.7.0 innstaller works, using synaptic now I have vlc, which is great, but Linux Mint or Ubuntu-studio 14.4 is not working.
Thank you, it was very helpful, especially if you have unstable internet connection.

---

### Post by Peter_R._Larsen on 2014-11-08
> **buzzingrobot said:**
> The overwhelming majority of Ubuntu packages are migrated over from Debian.  Even more of Mint is built directly on Ubuntu packages. Applications available in one of those distributions are almost always available for installation in the usual way in the others, although the specific versions can vary from release to release.

Installing a package is seldom a matter of just copying a single file. Applications usually contain any number of files, and the packages that we use to install them include data and scripts to make sure all the pieces end up in the right spots in the filesystem.   Any other packages -- the dependencies -- needed will be downloaded and installed *if we use* programs created to do that, like the Software Center, apt, Synaptic, etc. 

Debian packages can be searched at packages.debian.org.  Ubuntu packages can be searched at packages.ubuntu.com.  Both show a package's dependencies, changelog, etc.

Mint packages are at packages.linuxmint.com.  Since Mint relies on Ubuntu repos, there are relatively few packages there, so they're browsable instead of searchable.

[EDIT:  But, yes, technically, packages can be downloaded and installed locally using Software Center, apt, etc. That should work using an Ubuntu package on Ubuntu, a Mint package on Mint, etc.  Trying to install a foreign package is risky for a number of reasons.]

Tried with software center with ubuntu live cd/dvd and linux mint didnt worked, but debian 7.7.0 dvd-1 with synaptic works

---

### Post by grahammechanical on 2014-11-08
Thinking about this a bit more and remembering the days before I got broadband. I use to install Ubuntu from DVDs provided by computer magazines and I would install without an internet connection. The DVD would be listed as a software source. And If I installed an application from the software centre I would be asked to put the DVD in the drive.

The place to look is System Settings>Software and Updates>Other Software tab. On my system there is a box to tick to make the Utopic Unicorn (14.10) DVD a software source or repository, in other words. I would guess that being disconnected from the internet would be necessary to force apt-get install or any GUI front-end to apt-get to look for an offline repository.

Regards.

---

### Post by buzzingrobot on 2014-11-08
> **Peter_R._Larsen said:**
> Tried with software center with ubuntu live cd/dvd and linux mint didnt worked, but debian 7.7.0 dvd-1 with synaptic works

Might be a difference in how packages are archived on the dvd's. I haven't done it lately, but Software Center and the others will install a package that's been previously downloaded from packages.ubuntu.com.  That won't help reduce bandwidth use since any dependencies will be pulled down.

Linux and Windows and OS X assume sufficient bandwidth is available, which is obviously not always the case. That's a bit of an Achille's Heel.

---

