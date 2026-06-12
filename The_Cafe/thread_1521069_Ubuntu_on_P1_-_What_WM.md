---
title: "Ubuntu on P1 - What WM?"
date: 2010-06-30
forum: The Cafe
---

### Post by BrokenKingpin on 2010-06-30
I am going to be installing Ubuntu on an old school Pentium 1 computer, and was trying to decide what DE/WM I should go with. I will be doing the initial install with the mini install and then adding in the DE/WM.

I was initially thinking XFCE, but even that might be a bit heavy for this thing. I was then thinking OpenBox or LXDE. What do you guys think?


UPDATE:

I could not even get the debian mini.iso to install on this thing. The computer has been junked.

---

### Post by RiceMonster on 2010-06-30
dwm

---

### Post by aeiah on 2010-06-30
you might be ok with a barebones openbox, but id suggest something even lighter if you can manage it. dwm, ion3, awesome

use the ubuntu minimal iso if you have a half-decent net connection and just sudo apt-get awesome. see if it runs

---

### Post by BrokenKingpin on 2010-06-30
DWM and Awesome DW look pretty cool, I will take a closer look at those, thanks.

Do you think a P1 running one of this DWs would have enough power to run some simple Gnome games?

---

### Post by Warpnow on 2010-06-30
I bet installing the gnome games will pull dependencies which will slow down the system. You're likely better off finding dependency-free games.

---

### Post by RiceMonster on 2010-06-30
> **Warpnow said:**
> I bet installing the gnome games will pull dependencies which will slow down the system. You're likely better off finding dependency-free games.

bsd-games ftw

---

### Post by Warpnow on 2010-06-30
> **RiceMonster said:**
> bsd-games ftw

[quote=wump]

Move or shoot? (m-s) s 10
*thwock!* *groan* *crash*

A horrible roar fills the cave, and you realize, with a smile, that you
have slain the evil Wumpus and won the game!  You don't want to tarry for
long, however, because not only is the Wumpus famous, but the stench of
dead Wumpus is also quite well known, a stench plenty enough to slay the
mightiest adventurer at a single whiff!!

[/quote]

Wump, wump, wump wump!

---

### Post by snowpine on 2010-06-30
Make sure you compare your system specs with the [Ubuntu System Requirements ]("https://help.ubuntu.com/community/Installation/SystemRequirements")to see if your project is realistic. 

A CLI-only Ubuntu install (with no windows manager or games) has the following requirements:

> # 300 MHz x86 processor
# 128 MiB of system memory (RAM)
# 1 GB of disk space
# Graphics card and monitor capable of 640x480
# CD-ROM drive

---

### Post by BrokenKingpin on 2010-06-30
> **snowpine said:**
> Make sure you compare your system specs with the [Ubuntu System Requirements ]("https://help.ubuntu.com/community/Installation/SystemRequirements")to see if your project is realistic. 

A CLI-only Ubuntu install (with no windows manager or games) has the following requirements:
Hmmm, I doubt it meets those. Any other Distros that might be better, say Debian net install?

---

### Post by snowpine on 2010-06-30
> **BrokenKingpin said:**
> Hmmm, I doubt it meets those. Any other Distros that might be better, say Debian net install?

Puppy Linux has [very low system requirements]("http://puppylinux.org/wikka/MinReq"): 

> Puppy has been tested on a very old machines but the best results for the standard release of Puppy Linux to run at a reasonable pace have been achieved with the following:

    * CPU : Pentium 166MMX
    * RAM : 128 MB physical RAM for releases since version 1.0.2 or failing that a Linux swap file and/or swap partition is required for all included applications to run; 64 MB for releases previous to 1.0.2 

Why don't you find out the specs of the machine and post back? :)

---

### Post by init1 on 2010-06-30
I was able to run Fedora Core 1 on 64MB. Gnome and KDE were extremely slow, but TWM was fast enough. You'll be swapping a bit if you try to run CLI Ubuntu, but it should work.

---

