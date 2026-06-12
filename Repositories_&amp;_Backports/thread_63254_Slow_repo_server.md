---
title: "Slow repo server"
date: 2005-09-07
forum: Repositories &amp; Backports
---

### Post by Buffalo Soldier on 2005-09-07
Anyone else experiencing slow downloads from repository servers? 

My download speed from repo servers has been around 2Kbps - 4Kbps this past few days. Thought at first perhaps something was wrong with my connection, but after did a few broadband speed test my average connection speed is around 700Kbps - 800Kbps. I'm on a 384/1024Kbps dsl connection.

Here's my sources.list file:```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Alpha i386 (20050831)]/ breezy main restricted

deb http://my.archive.ubuntu.com/ubuntu breezy universe main restricted
deb-src http://my.archive.ubuntu.com/ubuntu breezy universe main restricted

deb http://my.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://my.archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security universe main restricted
```

---

### Post by TheDanMan on 2005-09-07
The problem may still be your DSL and broadband test are not always a good indicator.  DSL has the tendency to fluctuate.  However I cannot deny that the repositories are slow themselves as I am on a slow connection at the moment.

Later (about 6 hours) when I'm back in the States, if someone has not verfied, I will do so.  Much more than that I cannot help.

---

### Post by Buffalo Soldier on 2005-09-07
[QUOTE=TheDanMan]The problem may still be your DSL and broadband test are not always a good indicator.  DSL has the tendency to fluctuate.  However I cannot deny that the repositories are slow themselves as I am on a slow connection at the moment.

Later (about 6 hours) when I'm back in the States, if someone has not verfied, I will do so.  Much more than that I cannot help.[/QUOTE]
 I guess you're probably right. already sent an email to my ISP... but I guess thats not gonna be much of a help either. Anyway, thanks for reply.

---

### Post by sheldonsenseng on 2005-09-24
apt reports your download speed in KBps and not in Kbps.

that means you have to divide your bandwidth by 8 to convert from Kbps to KBps.

And probably, your dsl provider is sharing your bandwidth with too many users.

[QUOTE=Buffalo Soldier]Anyone else experiencing slow downloads from repository servers? 

My download speed from repo servers has been around 2Kbps - 4Kbps this past few days. Thought at first perhaps something was wrong with my connection, but after did a few broadband speed test my average connection speed is around 700Kbps - 800Kbps. I'm on a 384/1024Kbps dsl connection.

Here's my sources.list file:```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Alpha i386 (20050831)]/ breezy main restricted

deb http://my.archive.ubuntu.com/ubuntu breezy universe main restricted
deb-src http://my.archive.ubuntu.com/ubuntu breezy universe main restricted

deb http://my.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://my.archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security universe main restricted
```[/QUOTE]

---

