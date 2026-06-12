---
title: "mutt-patched will get removed by update of mutt"
date: 2016-10-05
forum: Ubuntu Development Version
---

### Post by wgarcia on 2016-10-05
Yakkety comes with a new version of the mail reader mutt:

```

$ apt-cache policy mutt
mutt:
  Installed: 1.6.0-1
  Candidate: 1.6.2-3
  Version table:
     1.6.2-3 500
        500 http://archive.ubuntu.com/ubuntu yakkety/main amd64 Packages
 *** 1.6.0-1 100

```

I use a version called mutt-patched that provides a sidebar and depends on mutt, but there is no 1.6.2-3 version available:

```

$ apt-cache policy mutt-patched
mutt-patched:
  Installed: 1.6.0-1
  Candidate: 1.6.0-1
  Version table:
 *** 1.6.0-1 100
        100 /var/lib/dpkg/status

```
so updating mutt will remove mutt-patched. I have put then the upgrade of mutt on hold until I'm able to upgrade also mutt-patched.

I checked in Debian to see if it was a matter of mutt-patched not having been packaged yet, but there is no version 1.6.2-3 either there of mutt-patched. Is there any way to request mutt-patched 1.6.2-3 in Ubuntu or there is no chance until they package it for Debian?

---

### Post by dino99 on 2016-10-05
Well such patches was added some times ago to get a more user friendly UI. 
[https://screenshots.debian.net/package/mutt-patched](https://screenshots.debian.net/package/mutt-patched)

Since newer versions have added features & fixes; and these old patches are no more justified i suppose.
 [http://www.mutt.org/doc/UPDATING](http://www.mutt.org/doc/UPDATING)

---

### Post by #&amp;thj^% on 2016-10-05
And this was added
> Statistics
637 other people were interested in this package here. The newest known version of this software is 1.6.0-1 (Information last updated about 10 hours ago.) 

Good Info: [http://www.mutt.org/](http://www.mutt.org/)

---

### Post by wgarcia on 2016-10-06
Thanks. I looks like the patches were finally merged but in version 1.7.0, so the version provided with yakkety (1.6.2-3) does still not have it. So I either wait for 1.7.0 to land in Ubuntu (probably for 17.04 if it lands in Debian before) or I figure out how to enter a bug report asking to update to 1.7.0, maybe there is luck.

---

### Post by mc4man on 2016-10-06
SRU's for these 9 month 'releases' are probably a tough nut to crack. And  people using 16.10 should be moving up to 17.04 anyway, likely not much too risk by doing so during dev rather than waiting 9 months.

---

### Post by wgarcia on 2016-10-06
That's true, mc4man, but I move to the dev release about 2 months before actual release, I'm so stupid as to use it as my main OS in all my devices so I wait at least until some of the freezes, but you're right, no problem.

---

### Post by mc4man on 2016-10-06
mutt 1.7.0 is [in Debian]("https://packages.debian.org/sid/mutt") now so you'll likely see it in 17.04 dev at some point. .

---

### Post by wgarcia on 2016-10-07
Actually today an upgrade landed for 1.6.2-3 and it has already the patches merged (after 15 years or so mut-patched got merged!) so everything is OK, and this is really [Solved].

---

