---
title: "Testing Lubuntu 12.10 (QQ) from Alpha1 - The Final Release in Oct"
date: 2012-06-19
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by amjjawad on 2012-06-19
[CENTER]
[IMG]http://i45.tinypic.com/1z3owid.jpg[/IMG]

[LEFT]
Hi,

Let's share our experience, test results, etc when it comes to Testing Lubuntu 12.10.

So far, all what I personally know about Lubuntu 12.10 is:

** 1- [The Wallpaper Contests]("http://ubuntuforums.org/showthread.php?t=2006643").**

** 2- Kernel:**

> > With Lubuntu 12.04, we have decided to go for the generic Kernel so
> what about 12.10?

It will be PAE-only kernel, unless we can hire a kernel dev to maintain
a non-PAE kernel for us (so, don't really count on it). It's a
project-wide decision (mean Ubuntu and all the family). It's nearly
impossible to go against it.

Regards,
Julien LavergneTo make it extra clear regarding the Kernel, I have explained that on the mailing list so I'll copy-paste the same text:

> Some old machines has **NON-PAE CPU**. If you have a Linux Distribution with a **PAE Kernel**, then that system will not be bootable on a machine with NON-PAE CPU.
 

During the development of 12.04, both Xubuntu and Lubuntu teams decided to go for a NON-PAE Kernel (Generic Kernel - run "uname -r" in the terminal) so those users with NON-PAE CPU will not have any problem and they still can use Lubuntu and Xubuntu 12.04.
 

Ubuntu Kernel Team has decided to drop the NON-PAE Kernel and go for PAE Kernel.
As per Julien, we can't go against that unless we hire a developer who can make it possible.
We don't have any database/numbers of how many users over there with a NON-PAE CPU, that is why I asked :)
 

Hope it helps :)
How to find out whether your CPU is PAE or not?

```
 grep --color=always -i PAE /proc/cpuinfo
```So far, I know only one user who has a NON-PAE CPU (Intel Pentium M) and I was thinking to create a Poll[1] but since ONLY one users has reported that, I don't think it's necessary, at least for now.

Thanks!

[1] [https://wiki.ubuntu.com/Lubuntu/CommunicationsTeam/Polls](https://wiki.ubuntu.com/Lubuntu/CommunicationsTeam/Polls)
[/LEFT]
[/CENTER]

---

### Post by jerrylamos on 2012-06-19
> 
So far, I know only one user who has a NON-PAE CPU (Intel Pentium M) and I was thinking to create a Poll[1] but since ONLY one users has reported that, I don't think it's necessary, at least for now.
Must be me.  I've got 2 lubuntu partitions running:
1. lubuntu precise "upgraded" to quantal, keeps old kernel.  Updates update a bunch of stuff some held back especially 3.4.0-5 no surprise.  Running O.K. wireless WPA et. al.
2. lubuntu precise change /etc/apt/sources.list from precise to quantal.  Updates update a bunch of stuff, more held back than 1., kernel stays with precise 3.2.0-24 (I think, I'm on another notebook right now)

They both say quantal when doing cat /proc/version.

They're both running I don't know for how long.  Fun anyway.

Jerry

---

### Post by amjjawad on 2012-06-19
> **jerrylamos said:**
> Must be me. 
Jerry

No Jerry, you would be the "2nd" user that I know so far :D

---

### Post by kalehrl on 2012-06-19
I believe I was the one who complained about PAE kernel in the future 12.10 on Lubuntu mail list. So you see, 2 users already. Maybe putting a poll makes sense. :)

---

### Post by Elfy on 2012-06-20
Closed - staff review.

---

### Post by philinux on 2012-06-21
Following a staff discussion it has been agreed to leave this closed as long threads containing multiple issues are not good for users to navigate and are unhelpful in general. Solutions to problems get hard to find after they grow to over 5 - 10 pages

Therefore please use the Lubuntu prefix for new issues/problems with one thread per issues. These can also then be marked solved where appropriate.

Regards.

---

