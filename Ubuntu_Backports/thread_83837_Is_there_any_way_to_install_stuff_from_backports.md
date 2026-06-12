---
title: "Is there any way to install stuff from backports?"
date: 2005-10-29
forum: Ubuntu Backports
---

### Post by Nasso on 2005-10-29
I need some of the software that is normally found on the backports. Is there any way to get them in a safe way through apt? Use the hoary backports or debian, is that safe? or do i have to compile or use other methods other then the packagesystem? (dont like to do that :( )

---

### Post by aysiu on 2005-10-29
My understanding is that the backports has only the latest versions of software that already exists in other repositories. Do you have Universe enabled?

---

### Post by Nasso on 2005-10-30
i think so?

i cant find mplayer, is it in universe?

is it safe to use the hoary backports in breezy?

> 
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe



---

### Post by metoo on 2005-10-30
It's in multiverse.
Don't think, that hoary stuff will work under breezy. They use different compiler versions AFAIK.
Debian sid has switched too, but you might end up getting dependency problems.
As usual, Marillat is you friend.

---

### Post by Nasso on 2005-10-30
[QUOTE=metoo]It's in multiverse.
Don't think, that hoary stuff will work under breezy. They use different compiler versions AFAIK.
Debian sid has switched too, but you might end up getting dependency problems.
As usual, Marillat is you friend.[/QUOTE]

marillat, is that a debian release? is it safe to use packages from it?

---

### Post by Xian on 2005-10-30
[QUOTE=Nasso]marillat, is that a debian release? is it safe to use packages from it?[/QUOTE]
It's okay to use the codecs. 
Not sure about the rest (probably not everything).

[QUOTE=Nasso]i cant find mplayer, is it in universe?[/QUOTE]

It is in multiverse. See below:

```
$ sudo apt-cache policy mplayer-386
mplayer-386:
  Installed: 1:1.0-pre7cvs20050716-0.1ubuntu9
  Candidate: 1:1.0-pre7cvs20050716-0.1ubuntu9
  Version table:
 *** 1:1.0-pre7cvs20050716-0.1ubuntu9 0
        500 http://us.archive.ubuntu.com breezy/multiverse Packages
        100 /var/lib/dpkg/status
```

---

