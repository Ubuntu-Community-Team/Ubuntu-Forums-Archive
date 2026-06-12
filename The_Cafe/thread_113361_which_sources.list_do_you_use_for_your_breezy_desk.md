---
title: "which sources.list do you use for your breezy desktop ?"
date: 2006-01-06
forum: The Cafe
---

### Post by ubuntu_demon on 2006-01-06
Hi,

I'm interested in desktop users running on breezy. I want to know what kind of sources.lists are popular. Here are the options :

* default sources.list or the default sources.list + universe/multiverse

* I use ubuntu_demon's sources.list / my recommended breezy sources.list
or one based on this sources.list. For more info see :
[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

* I use source-o-matic or one based on this sources.list. For more info see :
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

* I use doc.gwos.org (Written by humanity_to_others Added by manicka) 
or one based on this sources.list. For more info see :
[http://doc.gwos.org/index.php/Sources.list](http://doc.gwos.org/index.php/Sources.list)

* I use automatix :
[http://ubuntuforums.org/forumdisplay.php?f=77](http://ubuntuforums.org/forumdisplay.php?f=77)

* I use easy ubuntu:
[http://ubuntuforums.org/forumdisplay.php?f=86](http://ubuntuforums.org/forumdisplay.php?f=86)

*other (please post the url or your sources.list)

Please explain why, what architecture you are on and what kind of user you are.
If you have included any "exotic" / "non-standard" repos that most of us don't know about please feel free to give us some info!

I'm a nerd / desktop user on the 686-smp kernel (p4 2.8c with HT). I use "my recommended breezy sources.list".

---

### Post by matthew on 2006-01-06
Mine is similar to U-B's and the gwos version, but occasionally I add something from [http://www1.apt-get.org]("http://www1.apt-get.org") if there is something specific I want and it is in a repo listed there. I'm hesitent to recommend that, though, because you can cause breakage to your system by doing that. In other words, if you don't know what you are doing, stick to the repos already listed in these lists!

EDIT: oh, yeah. I voted "other."

EDIT2: there are some others listed here: [https://wiki.ubuntu.com/BreakMyUbuntu](https://wiki.ubuntu.com/BreakMyUbuntu) and the same caveat applies. Don't use them if you aren't prepared to fix breakage!!

---

### Post by ubuntu_demon on 2006-01-06
matthew thnx for the info.

why don't you download the packages by hand (from the repos you find in apt-get.org) instead of including the repo in the sources.list ?

Also IMHO if a package is available somewhere requesting a backport helps everyone.

---

### Post by Kimm on 2006-01-06
Other, this is my sources.list

```

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

deb [http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx](http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx) ./

deb [http://download.gna.org/wormux/package/debian/](http://download.gna.org/wormux/package/debian/) /
deb-src [http://download.gna.org/wormux/package/debian/src/](http://download.gna.org/wormux/package/debian/src/) / 

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main

deb [http://sentinel.dk/debian/](http://sentinel.dk/debian/) unstable main

deb [http://soulmachine.net/breezy](http://soulmachine.net/breezy) unstable/

deb [http://www.davidpashley.com/debian/irssi-sarge/](http://www.davidpashley.com/debian/irssi-sarge/) ./

#mono
deb [http://debian.meebey.net/](http://debian.meebey.net/) ./

```

---

### Post by Kvark on 2006-01-06
I use the default with universe, multiverse plus backports added and cdrom removed cause synaptic got annoying by asking for the CD.

---

### Post by DimaIL on 2006-01-06
[QUOTE=Kimm]Other, this is my sources.list
...
[/QUOTE]

How can i see which package there are in your sources.list?
and How have u found this sources?

Thanks!
Dima

---

### Post by Kimm on 2006-01-06
> 
How can i see which package there are in your sources.list?
and How have u found this sources?


If you want to see the packages, I supose you have to add them, or, try to interpret the urls. I have sources for the latest version of mono (commented), debian repository for VLC and wine. I dont know aout all of them

I found the sources here and there, some places provide apt-get servies for their software, so I usualy add it.

---

### Post by DariusTriplet on 2006-01-06
I use the default + uni/multiverse, along with Wine's repository.

---

### Post by matthew on 2006-01-06
[quote=ubuntu_demon]matthew thnx for the info.

why don't you download the packages by hand (from the repos you find in apt-get.org) instead of including the repo in the sources.list ?

Also IMHO if a package is available somewhere requesting a backport helps everyone.[/quote]I've done all these...but once in a while I find a repo that has more than one or two things I want and I just give it a go. I have made multiple backport requests, but the program has to be in the development version (currently Dapper) before it can even be backported and on occasion I've found things that don't qualify.

Anyway, great recommendations.

---

### Post by ubuntu_demon on 2006-01-07
If you have included any "exotic" / "non-standard" repos that most of us don't know about please feel free to give us some info!

---

### Post by tseliot on 2006-01-08
I use Automatix's sources.list because I don't have much time to install each package and to add the repos myself.

I use Ubuntu Breezy 32bit.

---

