---
title: "Sources"
date: 2005-04-06
forum: Repositories &amp; Backports
---

### Post by Nez7165 on 2005-04-06
Can anyone please give me a full list of sources for hoary so that i can update my sources and get all the unaficial pacages and the better upgrades. Thanks

---

### Post by Joeb on 2005-04-06
I believe that if you edit yout /etc/apt/sources.lst and change all of the references from warty to hoary, you have the full list of sources.

---

### Post by Nez7165 on 2005-04-06
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330)]/ hoary main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe


Thats what my sauses look like. I have uncomited some of the bottem ones 2 get more packeges. But i still dont have all the sources i had before i reinstalled my pc to hoary. i cant get mplayer and other things. If you use Hoary plaese tell me what im missing.

---

### Post by lao_V on 2005-04-06
You can add multiverse in the end (after universe)

---

### Post by Nez7165 on 2005-04-06
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330)]/ hoary main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe multiverse

# Englightenment DR17
deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/
#deb-src [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/


I found and added these. 
The multi universe can u please give me the codes for them so i can add it. Thanks

---

### Post by audax321 on 2005-04-06
Here's my sources, multiverse is listed in their as well

```

#deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted

#------------ UBUNTU REPOS ------------#

##############(default, all uncommented)
############# Ubuntu Hoary ##############

deb http://archive.ubuntu.com/ubuntu/ hoary main
deb http://archive.ubuntu.com/ubuntu/ hoary universe
deb http://archive.ubuntu.com/ubuntu/ hoary multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary restricted

deb-src http://archive.ubuntu.com/ubuntu/ hoary main
deb-src http://archive.ubuntu.com/ubuntu/ hoary universe
deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hoary restricted

##############(default, first two in each uncommented)
############## Ubuntu Security ##############

deb http://security.ubuntu.com/ubuntu/ hoary-security main
deb http://security.ubuntu.com/ubuntu/ hoary-security restricted
# deb http://security.ubuntu.com/ubuntu/ hoary-security universe
# deb http://security.ubuntu.com/ubuntu/ hoary-security multiverse

deb-src http://security.ubuntu.com/ubuntu/ hoary-security main
deb-src http://security.ubuntu.com/ubuntu/ hoary-security restricted
# deb-src http://security.ubuntu.com/ubuntu/ hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu/ hoary-security multiverse

################(default, all commented)
############## Ubuntu Hoary Updates ################

# deb http://archive.ubuntu.com/ubuntu/ hoary-updates main
# deb http://archive.ubuntu.com/ubuntu/ hoary-updates restricted
# deb http://archive.ubuntu.com/ubuntu/ hoary-updates universe
# deb http://archive.ubuntu.com/ubuntu/ hoary-updates multiverse

# deb-src http://archive.ubuntu.com/ubuntu/ hoary-updates main
# deb-src http://archive.ubuntu.com/ubuntu/ hoary-updates restricted
# deb-src http://archive.ubuntu.com/ubuntu/ hoary-updates universe
# deb-src http://archive.ubuntu.com/ubuntu/ hoary-updates multiverse

#------------ NON-UBUNTU REPOS ------------#

############(default, all commented)
########### Individual Packages ############

## Packages: lame, lame-dev, lame-extras, liblame0, lame-ha, lame-dev-ha, lame-extras-ha, liblame0-ha, xmms-musepack, xmms-musepack-386, xmms-musepack-k7, cue2toc, libaudio-wav-perl, shntool, shorten, xmms-shn
deb http://rarewares.org/debian/packages/unstable/ ./

## http://marillat.free.fr/ (MPlayer, Video Streaming, Windows avi/divx/etc codecs, Avidemux, etc.)
deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

## Hoary-Backports
# deb http://ubuntu-bp.sourceforge.net/ubuntu/ hoary-backports main universe

## Java 1.5
deb http://ubuntu.tower-net.de/ubuntu/ warty java

## Misc stuff
# deb http://apt.cerkinfo.be/ unstable main contrib non-free
# deb-src http://apt.cerkinfo.be/ unstable main contrib non-free

## GnomeBaker
# deb http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/releases/i386/ ./

```

---

### Post by bored2k on 2005-04-06
[QUOTE=Nez7165]Can anyone please give me a full list of sources for hoary so that i can update my sources and get all the unaficial pacages and the better upgrades. Thanks[/QUOTE]
 Nez, FAQ/HowTo is not the place for questions. The ones that posted should have known that also..

---

