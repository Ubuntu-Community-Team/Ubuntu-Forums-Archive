---
title: "xubuntu - How do I install wine?"
date: 2010-11-04
forum: Wine
---

### Post by Jynks on 2010-11-04
Hi there... 

I'm a new user of xubuntu and I am not sure how to install wine. The "Ubuntu software center" can find wine if I use it though the wine website itself says to do something totally different..

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
> Alternative Command Line Instructions for Installing Wine:

It is also possible to add the Wine PPA and install via the terminal. This may be useful on Kubuntu, Xubuntu, and other Ubuntu derivatives.

sudo add-apt-repository ppa:ubuntu-wine/ppa

Then update APT's package information by running 'sudo apt-get update'. You can now install Wine by typing 'sudo apt-get install wine1.3'.

If you'd like to browse the PPA manually, you can visit its Launchpad page.

So I am all confused.... how should I install this?

---

### Post by cogadh on 2010-11-04
Either method will work. The Ubuntu software center will give you the current stable version of Wine, 1.2.1, while the WineHQ method will get you the most current unstable version, 1.3.6 as of this writing. Whichever one you use is up to you. The stable version does not get updates beyond critical fixes, while the unstable is updated roughly every two weeks. The unstable one is a bit risky since the frequent updates can sometimes introduce new bugs to Wine, but it might have greater support for Windows software.

---

### Post by Jynks on 2010-11-04
ok... I got the "unstable" version.... but now what dosn't seam to put anything in the "start menu" or w/e that is called in xubuntu

---

### Post by cogadh on 2010-11-04
You might need to logout/login to see the menu change.

---

### Post by lkjoel on 2010-11-05
> **Jynks said:**
> ok... I got the "unstable" version.... but now what dosn't seam to put anything in the "start menu" or w/e that is called in xubuntu
xubuntu might not display it.

---

