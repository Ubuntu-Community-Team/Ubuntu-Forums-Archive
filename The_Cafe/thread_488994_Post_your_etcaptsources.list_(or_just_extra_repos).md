---
title: "Post your /etc/apt/sources.list (or just extra repos)"
date: 2007-06-30
forum: The Cafe
---

### Post by FoolsGold_MKII on 2007-06-30
I hope there aren't any other threads around here with the same idea, so here goes:

I'm curious to see what extra repositories people have added to their apt sources list. It might be useful to have a whole lot of lists here in case people wish to examine repositories they didn't know of, so it's of practical benefit too.

You don't have to post the entire source.list file if you don't want - we don't need official repos for Ubuntu for example, mainly extra repositories. I'll start:

```
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs...
deb http://download.tuxfamily.org/3v1deb feisty eyecandy 
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

# Medibuntu - Ubuntu 7.04 "Feisty Fawn"
# Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free

# Iuculano's debian packages - Ubuntu 7.04 "Feisty Fawn"
deb http://ubuntu.iuculano.it feisty thunderbird

# WineHQ APT Repository - Ubuntu 7.04 "Feisty Fawn"
deb http://wine.budgetdedicated.com/apt feisty main
deb-src http://wine.budgetdedicated.com/apt feisty main

# Ubuntu Screenlets repository - Ubuntu 7.04 "Feisty Fawn"
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
```

---

### Post by reacocard on 2007-06-30
```
## Reacocard's packages
## WARNING: Some components may be unstable or replace standard Ubuntu packages.
## http://syzygy42.tuxfamily.org/
## GPG: http://download.tuxfamily.org/syzygy42/8434D43A.gpg
deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator closure exaile exaile-svn gstreamer-equalizer reacocard
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator closure exaile exaile-svn gstreamer-equalizer reacocard

## Treviño's Suspend2 Packages
## WARNING: Replaces standard Ubuntu kernel-related packages
## http://ubuntuforums.org/showthread.php?p=2520472
## GPG: http://download.tuxfamily.org/3v1deb/DD800CD9.gpg
deb http://download.tuxfamily.org/3v1deb feisty suspend2
deb-src http://download.tuxfamily.org/3v1deb feisty suspend2

## Treviño's EyeCandy Repository
## WARNING: May be unstable
## http://forums.opencompositing.org/viewtopic.php?f=14&t=131
## GPG: http://download.tuxfamily.org/3v1deb/DD800CD9.gpg
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

## Medibuntu
## WARNING: Contains software that may be illegal in some areas.
## http://www.medibuntu.org/
## GPG: http://packages.medibuntu.org/medibuntu-key.gpg
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## Improved Subpixel Font Rendering
## WARNING: replaces libcairo, libxft and libfreetype
## http://ubuntuforums.org/showthread.php?t=343670
## GPG: http://www.telemail.fi/mlind/ubuntu/937215FF.gpg
#deb http://www.telemail.fi/mlind/ubuntu feisty fonts
#deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts
```

In case you're wondering what all those components on my repo (the first one) are, you can find a full list with descriptions here: [http://syzygy42.tuxfamily.org/dists/feisty/](http://syzygy42.tuxfamily.org/dists/feisty/)

GPG Keys can be imported with this command (replace URL with the key's address)
```
wget -q URL -O- | sudo apt-key add -
```

---

### Post by ~LoKe on 2007-06-30
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

# Treviño's Ubuntu gutsy EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs...
## deb http://download.tuxfamily.org/3v1deb feisty eyecandy
## deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

---

### Post by Polygon on 2007-06-30
Exaile repo
Google Desktop repo
automatix repo 

(if  anyone makes ONE COMMENT about automatix i will slay you where you stand. have a nice day.)

---

### Post by reacocard on 2007-06-30
> **Polygon said:**
> (if  anyone makes ONE COMMENT about automatix i will slay you where you stand. have a nice day.)

# Automatix

<!-- Automatix -->

/* Automatix */

// Automatix


:D

---

### Post by pseudonym on 2007-06-30
Other than the standard repos - ```
## SWIFTFOX (it actually *is* faster)
deb http://getswiftfox.com/builds/debian unstable non-free

## MEDIBUNTU (is it just me, or does this sound like some pill or cough mixture? )
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
# deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (never seems to be up ???)
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
# deb http://archive.canonical.com/ubuntu feisty-commercial main

## LOCAL REPO (you can't always trust 'sudo dpkg -i' to do it right. howto can be found [here]("http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages")  needs dpkg-dev to be installed)
deb file:/usr/local debs/

## DEBIAN MULTIMEDIA (for LAME 3.97 and Realplayer *only* )
# deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main 
```> **Polygon said:**
> Exaile repo
Google Desktop repo
automatix repo 

(if  anyone makes ONE COMMENT about automatix i will slay you where you stand. have a nice day.)
and, as I was just going to say about 'automatix'.... :D

---

### Post by juxtaposed on 2007-06-30
# 
# deb cdrom:[Debian GNU/Linux 4.0 r0 _Etch_ - Official i386 DVD Binary-1 20070407-11:40]/ etch contrib main

# deb cdrom:[Debian GNU/Linux 4.0 r0 _Etch_ - Official i386 DVD Binary-1 20070407-11:40]/ etch contrib main

deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib
deb-src [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib

deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) etch main contrib non-free
deb-src [http://ftp.debian.org/debian](http://ftp.debian.org/debian) etch main contrib non-free

---

### Post by solid0409 on 2007-07-01
```
#
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse


#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs...
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main
```



***_[SIZE=3]I think i have alot[/SIZE]_***

---

### Post by corney91 on 2007-07-01
```
#
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070627)]/ gutsy main restricted
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main
```

---

### Post by PriceChild on 2007-07-01
[COLOR=Red]_**It is NOT cool to have lots of repositories.**_[/COLOR]

Please remember someone can just add trojans to their repositories and is **has** been seen on this forum.

You must trust every software source you have... do not blindly add repositories off of this list.

---

### Post by reacocard on 2007-07-01
> **PriceChild said:**
> [COLOR=Red]_**It is NOT cool to have lots of repositories.**_[/COLOR]

Please remember someone can just add trojans to their repositories and is **has** been seen on this forum.

You must trust every software source you have... do not blindly add repositories off of this list.

Absolutely true. I am pretty sure none of the ones on my list have any trojans, etc. on them, as I know the maintainers of all of them (except medibutntu, but I don't think that's an issue.)

---

### Post by Alpha_toxic on 2007-07-01
```
# Main
deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe

deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe

deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse universe

# Beryl (I don't use Beryl right now)
# deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

# KDE (fast official local mirror)
deb [ftp://kde.paralax.org/kde/stable/3.5.7/kubuntu/](ftp://kde.paralax.org/kde/stable/3.5.7/kubuntu/) feisty main

# Medibuntu
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

# Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
```

---

### Post by FoolsGold_MKII on 2007-07-01
> **PriceChild said:**
> [COLOR=Red]_**It is NOT cool to have lots of repositories.**_[/COLOR]

Please remember someone can just add trojans to their repositories and is **has** been seen on this forum.

You must trust every software source you have... do not blindly add repositories off of this list.
Indeed. I never said that having lots of repositories was a good thing though; I simply want to see what repositories are out there, and for others to see, so that we can examine them ourselves and judge if they're useful and safe for our purposes. That's all.

---

