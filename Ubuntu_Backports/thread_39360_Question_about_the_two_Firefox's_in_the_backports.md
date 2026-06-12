---
title: "Question about the two Firefox's in the backports"
date: 2005-06-04
forum: Ubuntu Backports
---

### Post by Darrena on 2005-06-04
I see that there are two firefox packages, mozilla-firefox and firefox.  What is the difference?

Thanks!

---

### Post by jdong on 2005-06-04
Due to Mozilla's trademark restrictions, Breezy had to rename their Firefox packages from "mozilla-firefox" to just "firefox".

The "firefox" package actually contains Firefox, while the "mozilla-firefox-*" packages are just dummy placeholders to preserve compatibility with Hoary.

---

### Post by AndyAWS on 2005-06-04
That's strange then...I installed the package called "firefox" and in the process "mozilla-firefox" was removed, but not replaced by a newer one.

Did I screw-up the upgrade?

---

### Post by AndyAWS on 2005-06-04
Actually the newest "mozilla-firefox" package I see is 1.0.4~5.04ubp1+1.0.2-0ubuntu1.

---

### Post by jdong on 2005-06-04
Don't worry. The new mozilla-firefox dummy is only installed when another package calls for it. :)

---

### Post by AndyAWS on 2005-06-04
Cool...but why doesn't it show up in Synaptic when I do a search for firefox?

---

### Post by AgenT on 2005-06-05
[QUOTE=AndyAWS]Cool...but why doesn't it show up in Synaptic when I do a search for firefox?[/QUOTE]

Uhhhh, because mozilla-firefox has the string "firefox" in it? I think you are confused. Dummy packages are there to look like regular packages except that they are empty. They are used to ease transition. That's why they are called dummy packages. Sort of like a crash test dummy! ;) (okay, maybe not)

---

### Post by BudBrain on 2005-06-06
[QUOTE=AgenT]Uhhhh, because mozilla-firefox has the string "firefox" in it?[/QUOTE]

Guess you misread his question. He said it does NOT show up when searching for "firefox".

The problem seems to be that there are no transition packages listed in Packages(.gz). Therefore apt does not know about them and the transition fails.
Just take a look at [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz) yourself. The packages are in the directory but not in the list. Perhaps a generation script is stumbling over the architecture "all" of those packages?

---

### Post by AgenT on 2005-06-06
[QUOTE=BudBrain]Guess you misread his question.[/QUOTE]

Ooops. :-#

---

### Post by jdong on 2005-06-07
[QUOTE=BudBrain]Guess you misread his question. He said it does NOT show up when searching for "firefox".

The problem seems to be that there are no transition packages listed in Packages(.gz). Therefore apt does not know about them and the transition fails.
Just take a look at [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz) yourself. The packages are in the directory but not in the list. Perhaps a generation script is stumbling over the architecture "all" of those packages?[/QUOTE]

> 
Package: firefox
Version: 1.0.4-1ubuntu2~5.04ubp2
Priority: optional
Section: web
Maintainer: Eric Dorland <eric@debian.org>
Depends: fontconfig, psmisc, debianutils (>= 1.16), libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.8.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.2.ds1-4), libcairo1 (>= 0.3.0), libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), libgcc1 (>= 1:4.0.0-7), libgconf2-4 (>= 2.9), libglib2.0-0 (>= 2.6.0), libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.6.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.90), libgtk2.0-0 (>= 2.6.0), libice6 | xlibs (>> 4.1.0), libidl0, libjpeg62, libkrb53 (>= 1.3.2), liborbit2 (>= 1:2.12.0), libpango1.0-0 (>= 1.8.1), libpixman1 (>= 0.1.3), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libsm6 | xlibs (>> 4.1.0), libstdc++6 (>= 4.0.0-7), libx11-6 | xlibs (>> 4.1.0), libxft2 (>> 2.1.1), libxinerama1, libxml2 (>= 2.6.17), libxrender1, libxt6 | xlibs (>> 4.1.0), zlib1g (>= 1:1.2.1)
Suggests: firefox-gnome-support (= 1.0.4-1ubuntu2~5.04ubp2), latex-xft-fonts, xprint
Conflicts: mozilla-firefox (<< 1.0.4)
**Provides: www-browser, ***mozilla-firefox*****
Replaces: mozilla-firefox (<< 1.0.4)
Architecture: i386
Filename: dists/hoary-backports/main/binary-i386/firefox_1.0.4-1ubuntu2~5.04ubp2_i386.deb
Size: 8545466
MD5sum: 6d08c8b1c87e06114b1f8952067db1cd
Description: lightweight web browser based on Mozilla
 Firefox is a redesign of the Mozilla browser component, similar to
 Galeon, K-Meleon and Camino, but written using the XUL user interface
 language and designed to be lightweight and cross-platform.
 .
 This browser was previously known as Firebird and Phoenix.
installed-size: 24300
mozilla-firefox is a provided virtual package :)

---

### Post by BudBrain on 2005-06-07
[QUOTE=jdong]mozilla-firefox is a provided virtual package :)[/QUOTE]

Yes, I see. But it does not give me a smooth transition.
First "firefox" should be installed automagically through a dummy package "mozilla-firefox" depending on "firefox". The same for "firefox-dev" and so on.
Second when I try to install "firefox" manually I get the following:
> rat@roadrunner:~$ LANG=C sudo apt-get -u --purge install firefox firefox-dev firefox-dom-inspector firefox-gnome-support
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libcairo1 libpixman1
Suggested packages:
  latex-xft-fonts xprint
The following packages will be REMOVED:
  devhelp* devhelp-book-autotools* devhelp-book-binutils* devhelp-book-cvs* devhelp-book-emacs* devhelp-book-gdb* devhelp-book-glibc* devhelp-book-gtk2*
  devhelp-book-make* devhelp-book-sdl* devhelp-books* libdevhelp-1-0* mozilla-firefox* mozilla-firefox-dev* mozilla-firefox-dom-inspector*
  mozilla-firefox-gnome-support*
The following NEW packages will be installed:
  firefox firefox-dev firefox-dom-inspector firefox-gnome-support libcairo1 libpixman1
0 upgraded, 6 newly installed, 16 to remove and 0 not upgraded.
Need to get 11.6MB of archives.
After unpacking 12.2MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
I think the libdevhelp-1-0 is the cause of the trouble:
> rat@roadrunner:~$ LANG=C apt-cache show libdevhelp-1-0
Package: libdevhelp-1-0
Priority: optional
Section: libs
Installed-Size: 220
Maintainer: Gustavo Noronha Silva <kov@debian.org>
Architecture: i386
Source: devhelp
Version: 0.9.3-1ubuntu2
Replaces: devhelp (<< 0.9-5)
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.8.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:4.0-0pre6ubuntu4), libgconf2-4 (>= 2.9), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.6.0), libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.6.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.90), libgtk2.0-0 (>= 2.6.0), libice6 | xlibs (>> 4.1.0), liborbit2 (>= 1:2.12.0), libpango1.0-0 (>= 1.8.0), libpopt0 (>= 1.7), libsm6 | xlibs (>> 4.1.0), libxml2 (>= 2.6.17), zlib1g (>= 1:1.2.1), **mozilla-firefox (>= 0.10)**, devhelp-common (= 0.9.3-1ubuntu2)
Conflicts: devhelp (<< 0.8.1-1)
Filename: pool/main/d/devhelp/libdevhelp-1-0_0.9.3-1ubuntu2_i386.deb
Size: 68138
MD5sum: 8efd56b5226b1501b9edf71ce3c726e4
Description: Library providing documentation browser functionality
 This library provides embedable widgets from the Devhelp program to
 be integrated in tools like the Anjuta IDE for browsing API reference
 documentation.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Guess, you would need a versioned "Provides: mozilla-firefox", if this is possible, or the already mentioned dummy package, which would also provide the automatic transition to "firefox". As there are such dummy packages in the directory already, I am wondering why they are not listed in Packages.gz.

I hope this was clear enough now :-)

---

### Post by BudBrain on 2005-06-09
Today an dist-upgrade did a smooth transition with the 1.0.4-1ubuntu2~5.04ubp2 versions.

Thank you :-)

---

