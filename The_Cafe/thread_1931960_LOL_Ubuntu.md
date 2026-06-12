---
title: "LOL Ubuntu"
date: 2012-02-26
forum: The Cafe
---

### Post by DeathShot on 2012-02-26
I just got this message which I thought was funny because it clearly hasn't been changed since the move from Gnome 2.
[IMG]http://i42.tinypic.com/sp9fyd.png[/IMG]

This brings back good old memories of Modern Warfare 2  errors in Modern Warfare 3

---

### Post by s3a on 2012-02-26
:) File it as a bug though please.

---

### Post by DeathShot on 2012-02-26
> **s3a said:**
> :) File it as a bug though please.
Erm... mind telling me how I do that :S

---

### Post by philinux on 2012-02-26
Open a terminal.

ubuntu-bug packagename

Not sure what the package is but the above is the universal way.

---

### Post by DeathShot on 2012-02-26
I tried a few things related to it but I guess none of them are packages because it specifically told me so. How am I supposed to know what package this is related to:confused: Is there like a general "error" or "notices" package? Actually what do you even mean by packages?

Would it help if I just told one of you guys how to do it?
Basically I googled why Alt-f2 wasn't working for me and found this thread: [http://ubuntuforums.org/showthread.php?t=1474589](http://ubuntuforums.org/showthread.php?t=1474589)

The thread obviously referred to the old Gnome2 days so I improvised, instead of system I went to Applications->Other->Keyboard Input Methods and when I clicked on that it told me that iBus was not started and do I want to start it yes or no. I clicked on yes and I get that. If I click on no it just quits and nothing happens.

I don't even know what iBus is, so I didn't mess around with it, instead I went the delete every hidden file in the home folder and log out and back in route... it did fix my problem.

---

### Post by philinux on 2012-02-26
If in doubt use ubuntu-bug linux and the launchpad guys will change it.

---

### Post by DeathShot on 2012-02-26
Ok. Bug report submitted. I feel good helping out :P

---

### Post by Paqman on 2012-02-26
> **DeathShot said:**
> Actually what do you even mean by packages?


A package is a discrete bundle of software. They're what your system downloads from the repos and installs when it does updates. On Ubuntu-like systems they have the file extension .deb. A package could be an application, a library used by apps, a bunch of files such as artwork, or even a "meta-package" that functions solely to control what other packages are installed.

You can search through all the available packages through a tool like Synaptic or online at [packages.ubuntu.com](packages.ubuntu.com).

---

### Post by DeathShot on 2012-02-26
Ahh, that is sort of what I thought. I have removed and added packages to my system then, but I still don't know how to find out which package was involved. There is an "ibus" package and a few others I tried, according to Synaptic Package Manager but Ubuntu-bug kept on telling me those things don't actually exist.

---

