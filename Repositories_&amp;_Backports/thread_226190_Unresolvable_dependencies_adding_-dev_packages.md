---
title: "Unresolvable dependencies adding -dev packages"
date: 2006-07-30
forum: Repositories &amp; Backports
---

### Post by 3point2 on 2006-07-30
Hi, I'm trying to add kdebase-dev, but Synaptic keeps complaining about unresolvable dependecies. I'm running Kubuntu Dapper (6.06) AMD64.
The problems are because an installed package is a newer version than its corresponding -dev package depends on.
For example, my installed libglib2.0-0 is a newer version than the libglib2.0-dev package (I think it was version 2.10.3 whilst the latest -dev package was 2.10.2). I decided to "force version" (i.e. downgrade) in order to install the dev package. Same exact thing with libqt3-mt and libqt3-mt-dev. Weirdly, the newer versions I had no longer appear in Synaptic after downgrading, i.e. I can't "un-force" my changes and go back to the version I had.
So this is Question 1: How did I end up with newer versions than those in the repositories? I remember when I used the "force version" option the current version was listed as "now" and the older version as "dapper". What's the difference between "now" and "dapper"? And why did Synaptic forget about my newer versions when I downgraded?

Anyway, my big problem is that I still can't install kdebase-lib because of the same type of versioning problem with libcupsys2. The installed version is 1.2.1-0ubuntu2 and libcupsys2-dev wants version 1.2.0-0ubuntu5. I try downgrade libcupsys from "1.2.1-0ubuntu2 (now)" to "1.2.0-ubuntu5 (dapper)", but then Synaptic also wants to remove a whole bunch of other packages, including cupsys, hpijs, kghostview, and kubuntu-desktop!
So, question 2: Why do all those other packages need to be removed?

Thanks for any help,
Basil.

This is my current repository setup:
deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted 
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted 
deb-src [http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted  
deb http://au.archive.ubuntu.com/ubuntu/ dapper universe multiverse 
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe multiverse 
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ dapper-security main restricted 
deb http://security.ubuntu.com/ubuntu/ dapper-security universe multiverse 
deb-src http://security.ubuntu.com/ubuntu/ dapper-security universe multiverse 
deb http://packages.freecontrib.org/plf/ dapper free non-free  
deb-src http://packages.freecontrib.org/plf/ dapper free non-free  
deb http://archive.canonical.com/ubuntu/ dapper-commercial main

---

### Post by seanf on 2006-08-19
Are you still stuck on this? I'm having the same problem, trying to downgrade libcupsys2 in order to get to the dev packages.

---

### Post by seanf on 2006-08-19
Just solved my own problem... you can get the correct libcupsys2-dev package from here:

[https://launchpad.net/distros/ubuntu/dapper/i386/libcupsys2-dev/1.2.2-0ubuntu0.6.06](https://launchpad.net/distros/ubuntu/dapper/i386/libcupsys2-dev/1.2.2-0ubuntu0.6.06)

I have no idea why it's not in Synaptic.

---

### Post by SlayerMan on 2006-09-28
Had the same problem. It still is not in synaptic as of today.

---

### Post by PabloH on 2006-09-29
I have noticed this issue with several dev packages, try installing the libgtk2.0  dev package, for example. The dev packages are lagging the release packages by a version. This is driving me totally nuts. Is there a reason for this? ](*,)  

Why are packages allowed to be released when the dev packages do not have a release canidate? They obviously have to have code, or you could not have built the stinking package to begin with. I am having to go and find packages in pool and do all kinds of crazy crap to get stuff to build. 

Ubuntu is easy to install and nice to use, but I never had these issues with Debian, not even unstable.

I am ready to give up, this is not usable for development at all.

---

