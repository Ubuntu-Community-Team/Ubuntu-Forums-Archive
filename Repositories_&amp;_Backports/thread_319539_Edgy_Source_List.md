---
title: "Edgy Source List"
date: 2006-12-15
forum: Repositories &amp; Backports
---

### Post by business.geek on 2006-12-15
Hi I would like to know if there is a recommended Edgy Source List somewhere?

Thanks

---

### Post by mEtho on 2006-12-17
actually, i would be very much interseted in this topic if someone could spare their 2 to 3 minutes to discuss it.

---

### Post by business.geek on 2006-12-18
Would like to bump this up a bit.  anyone care to share any info regarding this topic?

---

### Post by insane_alien on 2006-12-19
i'm using the dapper recommended sources.

changed 'dapper' to 'edgy' obviously other wise it wouldn't work. i've also got a few more sources that can be a bit dodgy sometimes.

---

### Post by Simian on 2006-12-19
I'm not quite sure if this helps, but below is mine, it's all standard though.
```



#deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe


```

---

### Post by bruenig on 2006-12-19
Recommended is a bit hard to determine. Here is my sources.list. It has all of the ubuntu maintained repositories except the commercial one, but the commercial one doesn't really have much in it.

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
```

---

### Post by business.geek on 2006-12-22
Any update for this post? any other contributors?

---

### Post by Hark3n on 2007-02-04
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

