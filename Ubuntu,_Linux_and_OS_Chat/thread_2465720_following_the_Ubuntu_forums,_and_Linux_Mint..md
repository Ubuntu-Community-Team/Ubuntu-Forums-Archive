---
title: "following the Ubuntu forums, and Linux Mint."
date: 2021-08-09
forum: Ubuntu, Linux and OS Chat
---

### Post by babakott on 2021-08-09
Hi. I run Linux Mint 20.2. I like to peruse the Ubuntu forums as well as the Mint forums. I learn a lot about Linux in general from reading threads. But my question is this. Since Mint is based on Ubuntu, will the fixes and tricks I learn on the Ubuntu forums always work in Mint? If not, what is the worst that may happen? Say I learn how to build a module and install it to the kernel on the Ubuntu forums, will that applied information royally screw up my Mint system?


Cheers.

---

### Post by QIII on 2021-08-10
> **babakott said:**
> 
Since Mint is based on Ubuntu, will the fixes and tricks I learn on the Ubuntu forums always work in Mint?

Not necessarily, which is why we have a Mint sub-forum.

> If not, what is the worst that may happen?

Impossible to say for sure, since the Mint developers are free to to go their own way.  But it's not likely you'd nuke your system.  But we have a Mint sub-forum.

> Say I learn how to build a module and install it to the kernel on the Ubuntu forums, will that applied information royally screw up my Mint system?

See above.  But we have a Mint sub-forum.

---

### Post by guiverc on 2021-08-10
Mint uses the *deb* packaging that is common with Debian & Ubuntu... so it means commands `dpkg`, `apt` and like commands are the same. 

 However whilst I tend to like treating *my* **Debian & Ubuntu** as the *exact same thin**g*, they are not. I always consider the differences (which maybe just that they release at different dates, thus packages will never align; Debian releases on *odd* years, Ubuntu LTS on *even* years so those never align - but that's not everything).  Not all my Ubuntu packages are from upstream Debian, even if a large majority of them are - ie. they never perfectly align (and I'm using *impish* here on my Lubuntu, and comparing toDebian *testing* which is frozen currently as Bullseye is about to drop!)

For Ubuntu & Linux Mint - one **huge **difference between then is Ubuntu is *runtime adjustment* free, where as Linux Mint is not.

If Ubuntu (Lubuntu, Xubuntu or [any *flavor* of Ubuntu]("https://ubuntu.com/download/flavours")) need to make a change, they can SRU that change and amend their packages... Linux Mint doesn't have write access to Ubuntu repositories, so has decided to continue using them (*rather than compile their own of everything*), and adjust them during execution via *runtime adjustments*.  This opens a slight *security hole*, but also means something things that work perfectly in Ubuntu (or any *flavor* of Ubuntu) won't in Linux Mint.  It also may mean the reverse (ie. what works in Linux Mint may not work in any Ubuntu).

Note: *Linux Mint don't use adjustments for all their packages - if the cost of the adjustments are too high, they'll create their own packages for those; this has effects to but I'll skip this*

Linux Mint could opt to create their own packages, but that would cost time, resources, etc so their use of the *[hack* or] *runtime adjustments* makes sense to me, but it's a difference and something to consider (additional security risk etc even if *small*). 

Linux Mint doesn't have the Security equivalent of Ubuntu (it's costs $) though they the packages they use from Ubuntu (excluding runtime *adjustments *influenced) that went through Ubuntu security audits they do benefit from too  (bill paid by upstream Ubuntu). Hey, if you note my distro you'll see I'm using Lubuntu where LXQt & most apps I use come from 'universe' that is lower security anyway.


Anyway **my point** is there are differences....  though for most things you could treat them as roughly equivalent (*like me with Debian & Ubuntu*), **but** **always mentally evaluate every decision as to those differences before you act on it** (ie. consider if Linux Mint *adjustments* influence the area where you're making changes, etc.).

---

### Post by grahammechanical on 2021-08-10
My advice to anyone who wants to experiment as a way of learning is to do so on a second installation of the Linux distribution they are using. Then if you mess up you still have a working operating system. Trying to fix what is broken is also a way of learning but if it is the work OS that is broken it is sometimes quicker to re-install. So, always protect your important data.

Linux Mint is not an official Ubuntu flavour. I do not know why Linux Mint is not officially recognized. There must be a reason. So, as stated above, do not assume the two distributions are the exactly same but with a different desktop environments and user interfaces.

Regards

---

### Post by scorp123 on 2021-08-10
> **grahammechanical said:**
>  I do not know why Linux Mint is not officially recognized. There must be a reason. 

Because back in 2007 Clem, the creator of Mint, started branching off several core packages towards his own versions, based on source code modified by him, compiled to packages that have a slightly different versioning scheme than the ones from Canonical. Also Mint maintains its own repositories and its releases have a different naming scheme. 

So instead of "Hirsute Hippo", "Focal Fossa", "Bionic Beaver" etc. Mint has "Uma", "Ulyssa", "Ulyana", "Tricia", "Tina" etc.  Just as Ubuntu can't be counted as an "official Debian release", you can't count Mint being anywhere close to being an "official" Ubuntu release.

---

