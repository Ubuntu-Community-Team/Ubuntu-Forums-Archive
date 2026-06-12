---
title: "Install multimedia packages on Dapper server"
date: 2008-07-04
forum: Server Platforms
---

### Post by osjak on 2008-07-04
**EDIT:** This issue has been resolved by upgrading to Ubuntu 8.04.1. [See this post.]("http://ubuntuforums.org/showpost.php?p=5328858&postcount=5")

Hi All,

I have been searching for multimedia packages in my server repositories, but cannot find much. For example:

```
admin@www1:~$ sudo apt-get install lame
Reading package lists... Done
Building dependency tree... Done
Package lame is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lame has no installation candidate
```


This is the overall list of what I need to install:

```
* LAME (http://lame.sourceforge.net)
* Mencoder and Mplayer (http://www.mplayerhq.hu)
  o AMR codec support (http://www.3gpp.org)
  o AC3 codec support (http://liba52.sourceforge.net)
  o AAC codec support (http://www.audiocoding.com)
  o MP3 codec support (http://lame.sourceforge.net)
  o OGG/Vorbis codec support (http://www.xiph.org/downloads/)
  o x264 codec support (http://www.videolan.org/developers/x264.html)
  o DivX/XviD codec support (http://www.xvid.org)
  o win32 codec support (http://www.mplayerhq.hu/MPlayer/releases/codecs/)
* FLVtool2 (http://rubyforge.org/projects/flvtool2/)
* ffmpeg-php 
```

This is my /etc/apt/sources.list
```
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
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe


# Seveas Packages - imbrandon mirror
#deb http://seveas.imbrandon.com dapper-seveas all
#deb-src http://seveas.imbrandon.com dapper-seveas all

# Seveas Packages - ubuntulinux mirror
#deb http://mirror.ubuntulinux.nl dapper-seveas all
#deb-src http://mirror.ubuntulinux.nl dapper-seveas all


# Media repositories
# Source: http://ubuntuforums.org/showthread.php?t=766683
deb http://packages.medibuntu.org/ dapper free non-free
deb-src http://packages.medibuntu.org/ dapper free non-free
```

I have never had to deal with multimedia on a server before and cannot find a good tutorial. I feel that all I'm missing is a correct repository source. After adding medibuntu.org to the list, nothing changed (I did run the update). Please help.

---

### Post by osjak on 2008-07-04
**UPDATE:**

Experimenting with Ubuntu Live CD I have found some repositories that allowed me to install lame, mencoder and mplayer:

```
deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse
```

I'm working on getting codecs installed at the moment. The one's that seem missing at /etc/mplayer/codecs.conf are: AMR, AAC, OGG/Vorbis

The packages that a still needed to be installed and I don't know how:
```
* FLVtool2 (http://rubyforge.org/projects/flvtool2/)
* ffmpeg-php
```

I would like to install them from a repository to get automatic updates later. Plan B would be to install them from sources, with no apt support for them. I'll update here on what I discover.

---

### Post by cariboo on 2008-07-04
Why not add medibuntu to your sources.list go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


and follow instructions for your distribution.

Jim

---

### Post by osjak on 2008-07-04
> **cariboo907 said:**
> Why not add medibuntu to your sources.list go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


and follow instructions for your distribution.

Jim
Jim, thank you for responding. Medibuntu is already in my sources.list (I included my sources.list in the first message). I had big hopes for that repository, but adding it didn't change anything. I'll keep it for now though.

---

### Post by osjak on 2008-07-06
I discovered that upgrading to 8.04.1 Hardy can be done with not much disturbance to the server. Here's the manual I used: 
[http://ubuntu-tutorials.com/2008/04/03/dapper-to-hardy-direct-server-upgrade-works/](http://ubuntu-tutorials.com/2008/04/03/dapper-to-hardy-direct-server-upgrade-works/)

Upgrade via SSH went smoothly with no glitches whatsoever. I'm really impressed with Ubuntu! This is the way to go!

I used the repositories form the article on upgrade above and added the same ones with "deb-src" in front of them to have access to source files. 

After that, installing all packages I mentioned in my first post was just a breeze. I additionally installed *ffmpeg* from the source with good options using this guide:
[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

Thank you all for reading and cariboo907 for trying to help.

---

### Post by osjak on 2008-07-07
An additional note:
After upgrading to 8.04.1 version, DenyHosts daemon failed to start after reboot. I noticed it by checking authorisation logs - thousands of brute force login attempts showed up again. I reinstalled DenyHosts and it is working fine again.

---

