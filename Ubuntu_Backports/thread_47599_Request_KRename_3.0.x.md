---
title: "Request: KRename 3.0.x"
date: 2005-07-09
forum: Ubuntu Backports
---

### Post by wantilles on 2005-07-09
Both for x86 and for amd64 architectures.

[http://packages.gentoo.org/search/?sstring=krename](http://packages.gentoo.org/search/?sstring=krename)

---

### Post by Seth on 2005-07-09
[QUOTE=wantilles]Both for x86 and for amd64 architectures.

[http://packages.gentoo.org/search/?sstring=krename](http://packages.gentoo.org/search/?sstring=krename)[/QUOTE]
 Here's x86.

[http://sethkinast.com/ubuntu/hoary/backports/krename_3.0.3-2build1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/krename_3.0.3-2build1~5.04ubp1_i386.deb)

---

### Post by ghostintheshell on 2005-07-13
Hi,

I installed it from source and it was easy (so, with a little linux experiment ;)).

Download the latest package [here](http://prdownloads.sourceforge.net/krename/krename-3.0.6.tar.bz2?download) (from the krename web site) 

First of all, uninstall any krename package if you already have one.

I had to install the kde libs to compile krename (via synaptic packages manager)
-> kdelibs4-dev (development files for the KDE core libraries)

Untar the downloaded file (krename-3.0.6.tar.bz2)
Move the new folder to /usr/local/src (sudo)
Go to /usr/local/src/krename-3.0.6 in a terminal
Type "./configure --prefix=/usr"
Type "make "
Type "sudo make install"
Optional: Type "make clean" (for disk space usage)

Test it: in a terminal type "krename &"
Optional: add a shortcut in the menu ;)

If you want to uninstall it, it's easy: 
Go to /usr/local/src/krename-3.0.6 in a terminal
Type "sudo make uninstall"
Optional: delete the folder (sudo)

That did the trick for me :)

I also installed some kde plugins from the synaptic packages manager (for mp3 tags reg. exp. and others I never used ;)).

I upgraded KDE 3.4.0 to 3.4.1 with success too.
(repositery: deb [http://kubuntu.org/hoary-kde341/](http://kubuntu.org/hoary-kde341/) hoary-updates main)

Good luck and enjoy!

---

