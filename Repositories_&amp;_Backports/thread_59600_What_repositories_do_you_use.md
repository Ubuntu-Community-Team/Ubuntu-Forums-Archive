---
title: "What repositories do you use?"
date: 2005-08-24
forum: Repositories &amp; Backports
---

### Post by acascianelli on 2005-08-24
I've been messing around with my repo's today and I tried cleaning up my sources.list file so its easier for me to understand.

.............................................................................................
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main universe multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main universe multiverse restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main universe multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main universe multiverse restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-security main universe multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-security main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main universe multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main universe multiverse restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) hoary/
.......................................................................................

I'm curious to see other people's source.list file to see where people are getting software/updates.

So please post your sources.list files :D

---

### Post by atilasendil on 2005-08-24
here is my nooby sources.list :-)

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by d1337 on 2005-08-24
Mostly exactly like the ubuntuguide.org repo list with the addition of the last backport entry which I added this evening in an attempt (ongoing) to work around the java issue that some folks seems to be having.

```
root@Tory:/etc/apt # cat sources.list
## deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
```

Curious, in comparison to your sources.list, I see that yours is simplified by univers, multiverse etc done on one line.  Does this still hit each repo?  I wasn't aware that this was possible.

---

### Post by acascianelli on 2005-08-24
[QUOTE=d1337]...

Curious, in comparison to your sources.list, I see that yours is simplified by univers, multiverse etc done on one line.  Does this still hit each repo?  I wasn't aware that this was possible.[/QUOTE]

I honestly have no idea, it seems like it does.

---

### Post by Unix_Wizard on 2005-08-29
[QUOTE=atilasendil]here is my nooby sources.list :-)

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe[/QUOTE]
 Is it possible to only update only repository without doing them all? I'm sort of in a mix with a network to another pc with slow dialup so I'd rather not wait for a massive update.

---

### Post by Yagisan on 2005-08-29
Mines a little bit different so I thought I'd post mine too.
```
deb http://au.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse

deb http://au.archive.ubuntu.com/ubuntu hoary-updates main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu hoary-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe multiverse

deb http://eyagi.bpa.nu/~jamie/ubuntu hoary main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu hoary main restricted universe multiverse
```The last repo is for the doomsday engine (a nice 3d doom sourceport) and it's resource packs, and doom megawads.

---

