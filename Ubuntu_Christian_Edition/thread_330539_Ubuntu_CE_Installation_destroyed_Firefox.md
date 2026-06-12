---
title: "Ubuntu CE Installation destroyed Firefox"
date: 2007-01-03
forum: Ubuntu Christian Edition
---

### Post by chaplanger on 2007-01-03
Due to a serious configuration problem with the video settings, I ended up doing a fresh install of Ubunto Edgy Eft.  Upon completion of setting up Ubuntu I then installed Ubuntu CE and Firefox was destroyed int he process  By destruction I am not referring to protocol problems etc, Firefox was simply 'gone' icons were gone and starting firefox up only produced an orange thumbnail of "unknown application".  This thumbnail could be resized to fill the screen but held no contents -- it was a blank window without any menu bars.

My question -- is this a known bug in the installation process? OR Did something just go terribly wrong in my installation routine (upon installing Ubuntu Ce -- it kept saying it could not find (various files -- mostly picture) from firefox.

Now that i have Ubuntu reinstalled again -- I am hesitant to reinstall CE -- is there a way to restore (as in WIN XP) to an earlier verson of the software if CE causes such a problem again.

For me CE is all about getting Gnomsword running (since I can't seem to get this installed any other way) -- Yet if this is not uncommon I will forgo this program for now.

---

### Post by meng on 2007-01-03
What other ways did you try to install gnomesword? What's wrong with the time-honored method of
1. enabling universe repositories
2. sudo aptitude install gnomesword

---

### Post by chaplanger on 2007-01-03
> **meng said:**
> What other ways did you try to install gnomesword? What's wrong with the time-honored method of
1. enabling universe repositories
2. sudo aptitude install gnomesword

I'm not certain what #1 requires, but running the command in #2 produces the following message:
The following packages have unmet dependencies:
  gnomesword: Depends: libsword5c2a (>= 1.5.8-7) which is a virtual package.

In previous attempts to install Gnomesword I ran into similar roadblocks -- ultimately my first installation of Ubuntu CE 'miraculously' installed Gnomesword!  

I see on the Gnomesword page that it requires version 1.5.9 version of Sword or later.  My problem is that I can get the 1.5.9 version tar, get it unpacked, but then have no idea how to run an install on this. . . Linux newbie here.

---

### Post by meng on 2007-01-03
Sorry, I forgot about that little wrinkle. It is however, a recognized (and solved) problem.
[http://www.ubuntuforums.org/showthread.php?t=285641](http://www.ubuntuforums.org/showthread.php?t=285641)
(otherwise search these forums for "gnomesword" and you'll find plenty of threads solved)

---

### Post by chaplanger on 2007-01-03
> **meng said:**
> Sorry, I forgot about that little wrinkle. It is however, a recognized (and solved) problem.
[http://www.ubuntuforums.org/showthread.php?t=285641](http://www.ubuntuforums.org/showthread.php?t=285641)
(otherwise search these forums for "gnomesword" and you'll find plenty of threads solved)

I appreciate the link -- however someting is wrong with the download page - none of the mirrors are accessible for this file  -- I keep getting 404 "Not Found" error windows on each and every mirror . . .

](*,)

---

### Post by chaplanger on 2007-01-03
I found a new address for the download -- I'l llet you know if this works

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fs%2Fsword%2Flibsword5c2a_1.5.8-8_i386.deb&md5sum=e01ce80113a18242be6de7b0806c017b&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fs%2Fsword%2Flibsword5c2a_1.5.8-8_i386.deb&md5sum=e01ce80113a18242be6de7b0806c017b&arch=i386&type=main)

---

### Post by chaplanger on 2007-01-03
Resolved this link allows for downloading of the needed file!

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fs%2Fsword%2Flibsword5c2a_1.5.8-8_i386.deb&md5sum=e01ce80113a18242be6de7b0806c017b&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fs%2Fsword%2Flibsword5c2a_1.5.8-8_i386.deb&md5sum=e01ce80113a18242be6de7b0806c017b&arch=i386&type=main)

---

