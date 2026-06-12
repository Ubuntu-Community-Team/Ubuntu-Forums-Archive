---
title: "Question: Building from source"
date: 2013-02-17
forum: The Cafe
---

### Post by IsshoNi on 2013-02-17
Is it possible when building/installing from a tar.bz2, that it will work on almost any architecture?

Here's what I want to do. I have an iBook G4 with YellowDog Linux 6.2 on it. It is a PowerPC. I want to install the xfce version 4.10 environment and use that rather than the older default environments (E17, Gnome, KDE, XFCE) that YellowDog Linux 6.2 comes with. 

Is it possible to install xfce 4.10 on a powerpc this way?

---

### Post by mamamia88 on 2013-02-17
> **IsshoNi said:**
> Is it possible when building/installing from a tar.bz2, that it will work on almost any architecture?

Here's what I want to do. I have an iBook G4 with YellowDog Linux 6.2 on it. It is a PowerPC. I want to install the xfce version 4.10 environment and use that rather than the older default environments (E17, Gnome, KDE, XFCE) that YellowDog Linux 6.2 comes with. 

Is it possible to install xfce 4.10 on a powerpc this way?

It's probably possible but probably not very simple.  You might want to consider another distro with it built in.   I know debian supports ppc and has an xfce version [http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/](http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/) but that has 4.8 and you would need to upgrade to sid or pull the xfce packages from sid.   Since debian supports power pc i'm guessing ubuntu should work?  Sorry no experience with yellow dog edit 4.10 is in experimental which means that you would just add experimental line to sources.list and do something like apt-get -t experimental install xfce4 to upgrade to it.   [http://packages.debian.org/search?keywords=xfce4&searchon=names&suite=all&section=all](http://packages.debian.org/search?keywords=xfce4&searchon=names&suite=all&section=all)

---

### Post by IsshoNi on 2013-02-17
> **mamamia88 said:**
> It's probably possible but probably not very simple.  You might want to consider another distro with it built in.   I know debian supports ppc and has an xfce version [http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/](http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/) but that has 4.8 and you would need to upgrade to sid or pull the xfce packages from sid.   Since debian supports power pc i'm guessing ubuntu should work?  Sorry no experience with yellow dog edit 4.10 is in experimental which means that you would just add experimental line to sources.list and do something like apt-get -t experimental install xfce4 to upgrade to it.   [http://packages.debian.org/search?keywords=xfce4&searchon=names&suite=all&section=all](http://packages.debian.org/search?keywords=xfce4&searchon=names&suite=all&section=all)

What is sid? Ubuntu and Lubuntu have issues with some of the hardware. Display problems, wireless networking problems, cpu scaling doesn't work, fan speed is buggy, and has temperature problems. I couldn't figure out how to fix them. The debian image might work, I'll give it a try.

---

### Post by mamamia88 on 2013-02-17
> **IsshoNi said:**
> What is sid? Ubuntu and Lubuntu have issues with some of the hardware. Display problems, wireless networking problems, cpu scaling doesn't work, fan speed is buggy, and has temperature problems. I couldn't figure out how to fix them. The debian image might work, I'll give it a try.

Debian has 3 branches stable which is the official release,testing which eventually turns into the next release, and unstable aka sid which is constantly receiving the latest and greatest packages that after certain conditions are met flow down to testing.   You can pull certain packages from unstable but still continue to use mostly testing stuff if you wish.  So if you know a package from experimental that you want you can install it but keep everything else at the testing level.  See [http://wiki.debian.org/DebianExperimental](http://wiki.debian.org/DebianExperimental)  edit: i see you are having problems with ubuntu.   Ubuntu is based on debian albeit with newer software.   You may or may not have the same problems on debian since they are somewhat cousins.

---

### Post by odiseo77 on 2013-02-17
In regards to the original question, I don't think you can compile a binary that works on any architecture, but you could always compile the latest version of XFCE on your YellowDog install (which would give you a powerpc-specific binary). 

Of course, it might be troublesome and you would likely have to compile and upgrade a large set of libraries and packages "by hand", so it's probably easier and more practical to install Debian Testing --which comes with xfce-4.8-- and pulling in xfce-4.10 from Debian's experimental repository afterward (with apt-get), as suggested by mamamia88.

Good luck.

---

