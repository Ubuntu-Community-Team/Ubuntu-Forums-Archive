---
title: "Hard Drive Space Required"
date: 2007-09-13
forum: Slackware and derivatives
---

### Post by rzrgenesys187 on 2007-09-13
I have a pretty old computer (4.7 g hard drive, not exactly sure about the other specs its at home and i'm at school) and i read slackware install should have 3.5GB of hard drive space.  I was wondering how large of an install it was, if it took up this 3.5 in which case it would be pretty useless to have a gig free.  I am trying to see how much i can get out of that old computer with linux, as well as to mess around with files i'm afraid to touch on my main laptop.

---

### Post by rivalarrival on 2007-09-13
I've never used it, but Damn Small Linux might be exactly what you're looking for...  I know people use old 486's as routers all the time.

But, I do have an old Pentium (no bloody 2, 3, or 4 after that) 133mhz and on old 4 gig hard drive lying around... And I'm feeling rather frisky this evening... :)

---

### Post by Pancetilla on 2007-09-14
Slackware's full install is huge! (around 4 GB of software), but you can always try another option (base install, custom..)...anyway, Slackware has no default package manager (apt-get, aptitude. synaptic-like) and you can get yourself into dependency hell if you don't know what you're doing...It's up to you.

I would go for something lighter, like Arch base install, then add xorg and the fluxbox with pacman.

---

### Post by rzrgenesys187 on 2007-09-14
Wow i figured slackware is good for an old system but i guess not this old.  I've looked into damn small linux before just wanted to have other options since i'm pretty much just going to be messing around on this computer, wanted to try a few different distros.  Thanks for the responses

---

### Post by saulgoode on 2007-09-15
I have Slackware 11 installed on a '486 with a 200Mb harddrive (about half of that available for my stuff). 

When SW says a full install, it means a FULL install and includes a lot of packages you can get by without. If you exclude the kernel source, Emacs, HOWTOs, scanner support, and KDE then you will free up quite a bit of disk space (KDE alone is over a gig of installs). If you exclude development tools you can eliminate about half a gig of space (even if you include GCC but get rid of the less popular languages such as FORTRAN, COBOL, and ADA then you have gained a lot).

I have not done a 'typical' install (I usually just install everything) but I believe that option only requires 1Gb of hard disk space.

---

