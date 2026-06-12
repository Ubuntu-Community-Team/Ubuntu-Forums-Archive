---
title: "How hard is custom?"
date: 2005-05-13
forum: The Cafe
---

### Post by benplaut on 2005-05-13
how hard is it to create a custom ubuntu-base distro? i have very little coding experience, but i need something that doesn't have gnome, but does have IceWM and XFCE. basically, i need something that would let the user be productive, but not let them break anything...

Firefox
XFCE
GUI config tools?
OOo 1.1.x
OOo pre2.0
XMMS
Mplayer
JRE
Totem

and that's about it...

is that something that would take a long time to make? or is there something like MySLAX to do it?

thankee!  :)

---

### Post by az on 2005-05-13
One way to go is to make a meta-package dor your ubuntu-based distro.  Call it custom-ubuntu-desktop or something.

Hack the ubuntu-desktop source package.  (Ubuntu-meta?)  Make your suctom desktop package depend on everything you need.  

Go to the internet-connected computer on which you want to install your OS and install a Hosry base system.  Enable universe as well as the repository containing your meta package (make a website with two finles in it - the deba and a Packages file) and install your custom package.  

If you want, you can hack the install cd so that all the packages are on it.  There is a customisation howto on the wiki...

---

### Post by Sam on 2005-05-13
Have a look [here](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#head-5f8244d5993c5060ca14eaa08005b9fcf6816be3-3).

---

### Post by jerome bettis on 2005-05-13
when you install, type server at the boot prompt.  this will do just a base install, then you can apt-get whatever you want, or do what they said above.  you could make a tarball of the entire filesystem and use a live cd to download and extract it on to the other computers.

---

