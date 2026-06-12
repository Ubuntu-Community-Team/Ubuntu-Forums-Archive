---
title: "Lubuntu: Did your upgrade work?"
date: 2019-01-05
forum: Ubuntu, Linux and OS Chat
---

### Post by rosika on 2019-01-05
Hi everybody and a Happy New Year,


I just wanted to ask: has anyone performed the UPGRADE from Lubuntu (64bit) 16.04(xenial) to 18.04(bionic)?
I mean the upgrade itself, not a clean install.
How did it go? Any problems?


I´m interested to learn about your views and experience before attempting an upgrade or clean-install.


Tnx in advance.
Rosika  :)

---

### Post by TheFu on 2019-01-06
Answers from other people won't really help determine whether your upgrade will be easy or not.  The specific programs and settings and hardware you have are unique. Those will determine, more than anything else, how clean the upgrade process goes.

For example, if you have lots of PPAs and use many 3rd party programs, then the upgrade is likely to have more issues.  If you take a stock 16.04 install with zero PPAs, no funny hardware, no encryption, no RAID disks, no new, odd hardware like nvme storage, well-supported network card and GPU, then it is likely to go much better.

A few days ago, I upgraded a 14.04 Lubuntu to 16.04 Lubuntu.  The process was fairly easy.
18.04 is too new for me.  Maybe in another year, it will be ok?

Regardless, if you do plan to do this upgrade, please, please, please, make a 100% know-you-can-recover backup of the system before starting.  Also, ensure the current system is 100%, fully, patched without any packaging errors.  Packaging errors do not get fixed/better by doing OS to OS updates.

---

### Post by Dennis N on 2019-01-06
Just for your information should you think about 18.10: An upgrade wasn't recommended from Lubuntu 18.04 to 18.10. You will likely get better results with a fresh install.
From the Lubuntu 18.10 release notes:
> ...upgrading Lubuntu from 18.04 to 18.10 causes a fair amount of issues. Therefore, we are not officially supporting this upgrade path at this time...

---

### Post by poorguy on 2019-01-08
I've never had good luck with upgrades on any OS as any previous problems always seem to move over with the upgrade or has been my experience.

I would suggest staying with an LTS distro.

---

### Post by rosika on 2019-01-14
Hi TheFu,

thanks for your views and comments. 
I understand I have to decide for myself what´s  going to work best for me.
Alas I can´t wait for another year as support for Lubuntu 16.04 LTS will stop in April this year. 
As far as backups are concerned, I perform a system backup with clonezilla once a month, so I´ve got that covered

Greetings
Rosika

---

### Post by rosika on 2019-01-14
Hello Dennis,

thanks for your answer.
I want to stick with LTS-versions. So an upgrade or fresh-install from 16.04 to 18.04 is my main concern.

Cheers
Rosika

---

### Post by rosika on 2019-01-14
Hello poorguy,

thanks for your reply.
What you pointed out is a concern to me, too. So I think a fresh install would be the way to go.
I´ll also want to stay with LTS.

Greetings
Rosika

---

### Post by TheFu on 2019-01-14
> **rosika said:**
> Hi TheFu,

thanks for your views and comments. 
I understand I have to decide for myself what´s  going to work best for me.
Alas I can´t wait for another year as support for Lubuntu 16.04 LTS will stop in April this year. 
As far as backups are concerned, I perform a system backup with clonezilla once a month, so I´ve got that covered

Greetings
Rosika

Sounds like you have this handled.

And for people thinking that Lubuntu is like all the other Ubuntu LTS with 5 yrs of support, [https://lubuntu.me/xenial-released/](https://lubuntu.me/xenial-released/) says:
>  Lubuntu 16.04 LTS will be supported until April 2019, with three years of support.
Xubuntu, Mate, Lubuntu all get 3 yrs of support.  It is only Server and the main "Ubuntu Desktop" (currently using Gnome3) which get the 5 yrs of support, which may be a surprise for many people.

An option worth considering for many would be to use the Linux Mint Desktop which is based on Ubuntu, but uses Cinnamon or Mate or KDE or Xfce DEs.  These are all LTS with 5 yrs. [https://linuxmint.com/download_all.php](https://linuxmint.com/download_all.php)   assuming you trust the Linux Mint team to be able to provide the necessary patches for that period.  I've seen complaints in the Mint community about GUI developers _moving one_ to newer releases before the 5 yr period is complete.  Since this can happen, it would make Mint effectively the same as Ubuntu support for the community DE versions.  Of course, the core programs and kernels would still be getting patched even if the DE doesn't.

Another option is to maintain your own DE/WM outside the Ubuntu family.  Suckless has a nice, simple, WM that is very small and unlikely to have security issues.  [https://dwm.suckless.org/](https://dwm.suckless.org/)  The latest version is from 2015. How's that for stable and bug free code?  Just an option.   I'm partial to fvwm myself, which has been around since the mid-1990s.

The point being, there are options.

---

### Post by rosika on 2019-01-16
Hi TheFu,

thanks for the additional info and the links. It´s always interesting to learn something new.

Greetings
Rosika

---

### Post by mastablasta on 2019-01-16
upgrade form 16.04 to 18.04 should be uneventful, however the next upgrade might get a bit rocky, since they will move form LXDE ot LXQT

---

### Post by rosika on 2019-01-18
Hi mastablasta,

thanks for your comment. 
Yes, that makes sense. As long as they stick to LXDE chances are that all might go well.

Greetings.
Rosika

---

