---
title: "Why don't Canonical switch Ubuntu Non-LTS with Rolling Release Model?"
date: 2018-05-07
forum: Ubuntu, Linux and OS Chat
---

### Post by dark. on 2018-05-07
I think it would be great if Canonical did that. :)

---

### Post by QIII on 2018-05-07
Hello!

Apparently Canonical does not share your appetite for that.  You're far from the first to say that it would be cool.

Rolling Ubuntu releases have been suggested and rumored for years.   But the factors weighing against it have always come down to about four:

1.  It is Debian-based and Debian is not a rolling release.  Ubuntu is, however, based largely on Debian Testing as it exists at the time of each Ubuntu development cycle.

2.  Ubuntu aims at stability -- and the 6 month releases are about as far from stable as they want to go.

3.  Broad hardware architecture support means a lot of testing.

4.  A very large package base in the repos means a lot of testing.

My crystal ball is broken and I have it in the shop right now, but if I had to guess I'd say a rolling release won't happen any time soon.

---

### Post by #&amp;thj^% on 2018-05-07
One night I had a "dream" that Ubuntu went the way of Arch and A new :KS Star was born>>>Ubuntu Rolling.:lolflag:
With a much more friendly Forum Base/Users like we have here! ;)

---

### Post by Skaperen on 2018-05-07
does rolling release mean the loss of long term support?

---

### Post by QIII on 2018-05-07
Not if an LTS is offered.

---

### Post by Skaperen on 2018-05-07
then what's the big deal about rolling-release?  within {12,14,16}.04 LTS i saw frequent updates and periodically 3rd number version increments.  what's wrong with this?

---

### Post by 1clue on 2018-05-07
> **Skaperen said:**
> does rolling release mean the loss of long term support?

They're mutually exclusive.

Look at this:   [https://www.howtogeek.com/192939/linux-distribution-basics-rolling-releases-vs.-standard-releases/](https://www.howtogeek.com/192939/linux-distribution-basics-rolling-releases-vs.-standard-releases/)

Both types of release play an important role in the Linux communities. Both have strengths and both have weaknesses. Ubuntu's 6-month schedule occupy the "standard release" category. Ubuntu's LTS releases go further than that.

In the development cycle of any package, you push a change to the package and people who follow the bleeding edge of that package start using it. And then the bug reports start coming. The developers will not have tried building it on every type of hardware, or with certain option combinations turned on. And then the compatibility with libraries of a certain version, and then interaction with different apps which changed in different, incompatible ways. Then people start fixing that, and the patches come in. People start using the patches and then it's a little better, but the patches also diverged some things so you need to do it again. And again. And people need to test it, not just automated scripts. So real-world use issues are found.

Rolling release distros follow the bleeding edge of packages. However they don't follow the REALLY bleeding edge because of the previous paragraph. They wait for a release to settle for a week or a month or 3 months, or better yet until a certain percentage of the bigger bugs get fixed. Then they pull in that version and try to integrate it with their distro. And the thing is, keeping a rolling release distro healthy is a lot of work for the users of that distro. You need to follow the news items and jump through certain hoops to get things working again, or to prevent their being broken in the first place.

A standard-release distro wants more stability than that. With the number of complaints I see on the forum here, many people seem to think that a standard-release distro is very unstable. In fact it's much more stable than a rolling release distro. A standard release distro is appropriate for homes and small businesses, or for specific niches where only a certain subset of things need to work reliably. A distro would focus on that market. I'm thinking firewalls and routers, for example. Most of the source tree we think of as Linux is irrelevant in those applications, so the distros tailored to that may have newer code than what might be mainstream.

An enterprise organization wants reliability over anything. They may install a server image and never do a major upgrade for the life of the hardware. Meaning they won't jump a major version. They instead keep applying patches to fix problems in the same old releases of their software. The premise behind LTS is that features have been frozen and only security or functionality fixes are pulled in. Theoretically that makes the distro more stable.

Ubuntu is controlled by Canonical. Canonical is a for-profit organization selling software solutions. They want stability, so they make Ubuntu LTS. LTS in the Ubuntu world means that the software is frozen at its major (upstream) version for 2 years before another LTS comes around, and is maintained at that version for 5 years. Which is about the expected shelf life of Enterprise hardware before they expect to replace those systems with something newer.

---

