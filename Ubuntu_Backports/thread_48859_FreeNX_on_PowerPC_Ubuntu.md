---
title: "FreeNX on PowerPC Ubuntu"
date: 2005-07-14
forum: Ubuntu Backports
---

### Post by supercleanse on 2005-07-14
I've tried pointing my sources.list at all of your mirrors and I still can't seem to find a package for FreeNX or nx out there...  Does that mean it doesn't exist for powerpc?  Here is my config for sources.list now:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-backports main universe multiverse restricted
deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-extras main universe multiverse restricted

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-backports main universe multiverse restricted
deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

if there is a powerpc package out there that I could install on my mac it would be great...

Thanks...

---

### Post by jdong on 2005-07-14
FreeNX does NOT compile under PPC.

---

### Post by Drain on 2005-08-03
[QUOTE=jdong]FreeNX does NOT compile under PPC.[/QUOTE]

That's interesting that you mention that - I was just reading this: [http://dot.kde.org/1120050176/](http://dot.kde.org/1120050176/)

...where the developers (Fabian Franz and Kurt Pfeifle) did a demo of FreeNX on a Power5/PPC64 machine with Kubuntu installed on it.

I also saw that [http://debian.tu-bs.de/project/kanotix/unstable/](http://debian.tu-bs.de/project/kanotix/unstable/) had some FreeNX packages for AMD64. (I attempted a quick install of that, but it requests nxagent and nxproxy which are said to be not installable). 

How far away from these pacakages are we?

---

### Post by Drain on 2005-08-04
[QUOTE=Drain]
How far away from these pacakages are we?[/QUOTE]

Heh. Nevermind, I was closer than I realized. I found some instructions on how to go about building FreeNX on Hoary here: 

[http://stateless.geek.nz/2005/06/27/building-freenx-04-on-ubuntu-hoary/](http://stateless.geek.nz/2005/06/27/building-freenx-04-on-ubuntu-hoary/)

And now I have it working on my AMD64. I'll be posting up my own howto in a little bit, and maybe that will be helpful to some other PPC users too.

---

