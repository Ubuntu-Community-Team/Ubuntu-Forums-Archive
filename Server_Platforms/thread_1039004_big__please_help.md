---
title: "big **** please help"
date: 2009-01-14
forum: Server Platforms
---

### Post by any.linux12 on 2009-01-14
Hey!

I did a big s*** in a ubuntu server 6.06 because when I entered via ssh I thought it was a 8.04 and changed the source.list. Now I lost all comands and I can't do a apt-get update and upgrade. I don't have ping, sh, nothing. please help

---

### Post by volkswagner on 2009-01-14
Here is my sources.list for 6.06 server.  I don't see how you lost all those commands, unless the update went through, and you upgraded packages with 8.04.  Sorry I am not sure how to fix that.

```
# 
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted
#deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by hyper_ch on 2009-01-14
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

P.S.: Keep this forum family-friendly.

---

### Post by freerkkalsbeek on 2009-01-14
Hmm. Sounds like your having a challenge.

Best thing is to boot the system from a live CD, mount your root filesystems in /mnt and then chroot into that.
After that, see if the damage can be repaired. 

Make sure that you mount /proc and /dev before starting repair actions in your chroot.
```

mount -t proc proc /mnt/proc
mount --bind /dev /mnt/bind

```

At least you can access your data/config that way.

---

### Post by any.linux12 on 2009-01-14
> **freerkkalsbeek said:**
> Hmm. Sounds like your having a challenge.

Best thing is to boot the system from a live CD, mount your root filesystems in /mnt and then chroot into that.
After that, see if the damage can be repaired. 

Make sure that you mount /proc and /dev before starting repair actions in your chroot.
```

mount -t proc proc /mnt/proc
mount --bind /dev /mnt/bind

```

At least you can access your data/config that way.

I'm backing up the system and then install again but thanks anyway ;)

---

### Post by any.linux12 on 2009-01-14
> **hyper_ch said:**
> It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

P.S.: Keep this forum family-friendly.

I just used Big **** to say that I realy needed help and as that I don't think that **** is such an offensive. By the way we live in the same country and here people say Scheisse (or whatever) all the time and yes I'm a foreign as probably 10% of the swiss population

---

