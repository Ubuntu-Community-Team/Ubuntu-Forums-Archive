---
title: "Post your Dapper sources.list"
date: 2006-08-10
forum: Repositories &amp; Backports
---

### Post by mmcmonster on 2006-08-10
Another Dapper sources.list.  Except for the PLF repository, which I just added, I've been using this without any problems on my Dapper desktop system for a few weeks now.:
```

# Ubuntu supported packages (packages, GPG key: 437D05B5)
# gpg --keyserver subkeys.pgp.net --recv 437D05B5
# gpg --export --armor 437D05B5 | sudo apt-key add -
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Dapper Backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Canonical Commercial packages
# Contains realplayer10, opera9, and other commercial projects
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

###
# Cipherfunk multimedia packages (GPG key: 33BAC1B3)
# gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
# gpg --export --armor 33BAC1B3 | sudo apt-key add -
# Contains some multimedia packages (w32codecs, libdvdcss2, etc.)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
#deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main

# Falcon Repositories
# Contains Mono, MythTV, many multimedia apps, and more.
# wget [http://ubuntu.moshen.de/2F306651.gpg](http://ubuntu.moshen.de/2F306651.gpg) -O- | sudo apt-key add -
#deb [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/) dapper all
#deb-src [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/) dapper all

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

# Seveas' packages (GPG key: 1135D466)
# gpg --keyserver subkeys.pgp.net --recv 1135D466
# gpg --export --armor 1135D466 | sudo apt-key add -
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas all
#deb-src [http://users.lichtsnel.nl/~seveas]("http://users.lichtsnel.nl/%7Eseveas") dapper-seveas all

###
# Cinelerra CV
# Only use 1 of the following 3 lines!
# i686:
#deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/]("http://www.kiberpipa.org/%7Egandalf/ubuntu/dapper/cinelerra/i686/") ./
# Athlon XP:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/]("http://www.kiberpipa.org/%7Egandalf/ubuntu/dapper/cinelerra/athlonxp/") ./
# Pentium 4:
#deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/]("http://www.kiberpipa.org/%7Egandalf/ubuntu/dapper/cinelerra/pentium4/") ./
# The following line is necessary for mjpegtools
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools]("http://www.kiberpipa.org/%7Egandalf/ubuntu/dapper/mjpegtools") ./

# Jahshaka real-time video editor
# Likely the second of these 2 lines is correct.
#deb [http://repo.jahshaka.org/ubuntu/dapper/binary-i386](http://repo.jahshaka.org/ubuntu/dapper/binary-i386) ./
deb [http://repo.jahshaka.org/ubuntu/dapper](http://repo.jahshaka.org/ubuntu/dapper) binary-i386/

# kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
# gpg --keyserver subkeys.pgp.net --recv DD4D5088
# gpg --export --armor DD4D5088 | sudo apt-key add -
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main
#deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

# kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)
# gpg --keyserver subkeys.pgp.net --recv DD4D5088
# gpg --export --armor DD4D5088 | sudo apt-key add -
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main
#deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main

# kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)
# gpg --keyserver subkeys.pgp.net --recv DD4D5088
# gpg --export --armor DD4D5088 | sudo apt-key add -
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main
#deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

# Opera browser
#deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

# Quod Libet, Rhythmbox, and Gaim recent releases, betas, and nightlies.
# gpg --keyserver pgp.mit.edu --recv-key D0AFFF5E937215FF
# gpg -a --export D0AFFF5E937215FF | sudo apt-key add -
deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) dapper main

# Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# XGL & compiz
# wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

``` 

By the way, does anyone have a GPG key for the PLF repositories.

---

### Post by ubuntu_demon on 2006-08-10
I moved your post to a new thread. IMHO it doesn't really belong to :
The discussion about my recommended Dapper sources.list :
[http://www.ubuntuforums.org/showthread.php?p=1076241](http://www.ubuntuforums.org/showthread.php?p=1076241)

---

### Post by ubuntu_demon on 2006-08-10
> **mmcmonster said:**
> Another Dapper sources.list.  Except for the PLF repository, which I just added, I've been using this without any problems on my Dapper desktop system for a few weeks now.:


I advise the average desktop user not to use PLF because :
- The PLF Ubuntu project is shutting down see : [http://plf.zarb.org/](http://plf.zarb.org/)
- It has not packages which aren't hosted elsewhere

> **mmcmonster said:**
> 
By the way, does anyone have a GPG key for the PLF repositories.

They are not available.

---

### Post by nismohasan on 2006-08-10
this is mine.

> # gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# dapper Backports (new software versions, provided by the Ubuntu Backports Project)

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

# Seveas' packages (packages, GPG key: 1135D466)
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

# Automatix
deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

# Bmpx
deb [http://files.beep-media-player.org/packages/ubuntu](http://files.beep-media-player.org/packages/ubuntu) dapper main universe
deb [http://thehoneymustardbandits.org/linux](http://thehoneymustardbandits.org/linux) dapper main universe

# Vlc nightlies
deb [http://nightlies.videolan.org/build/dapper-i386](http://nightlies.videolan.org/build/dapper-i386) /

# ntfs-3g & fuse-2.5 repo:
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) dapper main

# initng 
deb [http://debian.space-based.de/debs/](http://debian.space-based.de/debs/) experimental main
deb-src [http://debian.space-based.de/debs/](http://debian.space-based.de/debs/) experimental main

# Bleeding edge wine packages (packages)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Bazaar-NG development (packages, GPG key: 1F44842D)
deb [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
#deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

# Falcon Repositories
deb [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/) dapper all

# Quod Libet, Rhythmbox, and Gaim recent releases, betas, and nightlies.
deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) dapper main


---

### Post by ubuntu_demon on 2006-08-10
Here's mine (it's stickied) :

**my recommended Dapper sources.list**
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

This is the source.list which I recommend for average users (as well as new users) running Dapper. The average user has no ppc or amd64. So this sources.list isn't intended for those architectures. This sources.list isn't intended for servers.

---

### Post by Uncle Spellbinder on 2006-08-11
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free


## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

## OpenOffice.org 2 final packages (packages)
deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./

## The Opera browser (packages)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

## Amarok
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main
deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

##Compiz
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by ubuntu_demon on 2006-08-11
**Don't make this a contest in how much repositories you can enable before your system is totally messed up.** You should enable as little repositories as needed. You should only enable repositories you trust.

This is just a general warning. 

For average users it's better to use a sources.list like this one :

my recommended Dapper sources.list
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

It has universe,multiverse,dapper-commercial and backports enabled on default. cipherfunk,wine and skype are also included but commented.

---

### Post by ubuntu_demon on 2006-08-11
> **Uncle Spellbinder said:**
> ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free


## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

## OpenOffice.org 2 final packages (packages)
deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./

## The Opera browser (packages)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

## Amarok
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main
deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

##Compiz
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
You don't need seperate repositories for opera and openoffice.org

opera is included in dapper-commercial.
Your openoffice.org repository has an older version than the one in Dapper.

---

### Post by HAARP on 2006-08-26
- sorry delete this post -

---

### Post by HAARP on 2006-08-26
- sorry delete this post -

---

### Post by HAARP on 2006-08-26
Sorry, I've posted in the discussion thread before discovering this. Delete my posts in the discussion thread please.

-original post-
If anyone wants a huge badass sources.list, use mine. 
**[size=16][color=#FF0000]USE WITH EXTREME CAUTION[/color][/size]**
Don't add everything at once. **New user shouldn't use this under any circumstance!** It'll give you plenty of upgradable packages, many of them you **won't** **WANT** to upgrade! Familarize yourself with package pinning. It could seriously **break** your system or be a **security risk**. **USE WITH CAUTION!**

**add this ```
APT::Cache-Limit "100000000";
``` to /etc/apt/apt.conf, else it will fail to update!**

```
# Official Ubuntu packages (GPG: 437D05B5)
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
# Ubuntu backports project (GPG: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
# Ubuntu proposed packages (GPG: 437D05B5)
#deb http://archive.ubuntu.com/ubuntu dapper-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu dapper-proposed main restricted universe multiverse

# Ubuntu commercial packages
deb http://archive.canonical.com/ubuntu dapper-commercial main
deb-src http://archive.canonical.com/ubuntu dapper-commercial main

# Official Debian packages (GPG: 2D230C5F)
deb http://ftp.debian.org/debian stable main non-free contrib
deb-src http://ftp.debian.org/debian stable main non-free contrib
deb http://security.debian.org/ stable/updates main non-free contrib
deb-src http://security.debian.org/ stable/updates main non-free contrib

# Official MEPIS packages
#deb http://apt.mepis.org/6.0/ mepis main

# kubuntu.org packages for the latest KDE version (GPG: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main
deb http://kubuntu.org/packages/koffice-latest dapper main
deb http://kubuntu.org/packages/amarok-latest dapper main
deb-src http://kubuntu.org/packages/kde-latest dapper main
deb-src http://kubuntu.org/packages/koffice-latest dapper main
deb-src http://kubuntu.org/packages/amarok-latest dapper main

# Kubuntu Germany
deb http://archive.czessi.net/ubuntu dapper main restricted universe multiverse preview
deb-src http://archive.czessi.net/ubuntu dapper main restricted universe multiverse preview
# -------
# wget http://archive.czessi.net/ubuntu/kczessi.gpg; sudo apt-key add kczessi.gpg

# Ubuntu Lite
deb http://blueeyedcreature.net/ubuntu ./

# Debuntu packages
deb http://repository.debuntu.org/ dapper multiverse
deb-src http://repository.debuntu.org/ dapper multiverse
# -------
# wget http://repository.debuntu.org/GPG-Key-chantra.txt; sudo apt-key add GPG-Key-chantra.txt

# Ubuntu Taiwan extra repository
deb http://apt.ubuntu.org.tw ubtw/
deb http://apt.ubuntu.org.tw ubtw-testing/
deb-src http://apt.ubuntu.org.tw ubtw/
deb-src http://apt.ubuntu.org.tw ubtw-testing/

# Ubuntu Dapper University Klagenfurt
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu uniklu-desktop uniklu-intern uniklu-nfsv4 uniklu-vserver ##uniklu-testing
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu uniklu-desktop uniklu-intern uniklu-nfsv4 uniklu-vserver ##uniklu-testing
# -------
# wget http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub; sudo apt-key add uniklu-debuild.pub

# Penguin Liberation Front
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free

# Bazaar-NG development (GPG: 1F44842D)
deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./
deb-src http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# A little too quiet
deb http://apt.alittletooquiet.net/staging dapper main
deb-src http://apt.alittletooquiet.net/staging dapper main

# Achim's Kubuntu packages
deb http://www.mpe.mpg.de/~ach/kubuntu/dapper ./
deb-src http://www.mpe.mpg.de/~ach/kubuntu/dapper ./

# Asher256's packages
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french
deb-src http://asher256-repository.tuxfamily.org dapper main dupdate french
deb-src http://asher256-repository.tuxfamily.org ubuntu main dupdate french

# Cafuego's packages (GPG: 969F3F57)
deb http://ubuntu.cafuego.net/ dapper-cafuego all bcm43xx
deb-src http://ubuntu.cafuego.net/ dapper-cafuego all bcm43xx

# Doc.Horn's packages
deb http://ubuntu.moshen.de dapper all
deb-src http://ubuntu.moshen.de dapper all
# -------
# wget http://ubuntu.moshen.de/2F306651.gpg -O- | sudo apt-key add -

# Gauvain's repository
deb http://gauvain.tuxfamily.org/repos dapper contrib
deb-src http://gauvain.tuxfamily.org/repos dapper contrib

# Geole's repository
deb http://ubuntu.geole.info/ dapper universe multiverse
deb http://ubuntu.geole.info/ dapper-backports main restricted universe multiverse
deb-src http://ubuntu.geole.info/ dapper universe multiverse
deb-src http://ubuntu.geole.info/ dapper-backports main restricted universe multiverse 
# -------
# wget http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg; sudo apt-key add geole.info-apt-key.gpg

# lprod packages
deb http://lprod.org/deb/dapper/ ./
deb-src http://lprod.org/deb/dapper/ ./

# MaXeR's repository (GPG: 35A92053)
deb http://repos.knio.it/ breezy main contrib non-free
deb-src http://repos.knio.it/ breezy main contrib non-free

# mlind's packages (GPG: D0AFFF5E937215FF)
deb http://www.elisanet.fi/mlind/ubuntu dapper main fonts
deb-src http://www.elisanet.fi/mlind/ubuntu dapper main fonts

# Morgoth Dapper backports
deb http://morgoth.free.fr/ubuntu dapper-backports main
deb-src http://morgoth.free.fr/ubuntu dapper-backports main
# -------
# wget http://morgoth.free.fr/ubports/dlsignkey.php; sudo apt-key add dlsignkey.php

# Raphink's unofficial packages
deb http://packages.raphink.net/ubuntu dapper main
deb-src http://packages.raphink.net/ubuntu dapper main
# -------
# wget http://packages.raphink.net/ubuntu/raphink.asc; sudo apt-key add raphink.asc

# seb128's repository
deb http://people.ubuntu.com/~seb128/deb ./
deb-src http://people.ubuntu.com/~seb128/deb ./

# SeerOfSouls
deb http://SeerOfSouls.com/ dapper e17 contrib
deb-src http://SeerOfSouls.com/ dapper e17 contrib
# -------
# wget http://seerofsouls.com/keys/hawkwind.asc; wget http://seerofsouls.com/keys/philip.asc
# sudo apt-key add hawkwind.asc; sudo apt-key add philip.asc

# Seveas' packages (GPG: 1135D466)
deb http://seveas.theplayboymansion.net/seveas dapper-seveas all
deb-src http://seveas.theplayboymansion.net/seveas dapper-seveas all

# Thomas' packages
deb http://thomas.enix.org/pub/debian/packages/ dapper main
deb-src http://thomas.enix.org/pub/debian/packages/ dapper main

# Treviño's repository (GPG: 81836EBF)
deb http://3v1n0.tuxfamily.org dapper 3v1n0
deb-src http://3v1n0.tuxfamily.org dapper 3v1n0
# -------
# wget http://3v1n0.tuxfamily.org/81836EBF.gpg -O- | sudo apt-key add -

# AfterBirth repository
deb http://www.voxpopulimedia.com/debian dapper main

# Audacious
deb http://vdlinux.sourceforge.jp/ experimental audacious
deb-src http://vdlinux.sourceforge.jp/ experimental audacious

# Automatix
deb http://www.getautomatix.com/apt dapper main
# -------
# wget http://www.getautomatix.com/apt/key.gpg.asc; sudo apt-key add key.gpg.asc

# Bleeding Edge Drivers
#deb http://www.albertomilone.com/drivers/dapper/legacy/32bit binary/
#deb http://www.albertomilone.com/drivers/dapper/nonlegacy/32bit binary/
# -------
# wget http://albertomilone.com/drivers/tseliot.asc; gpg --import tseliot.asc; gpg --export --armor albertomilone@alice.it | sudo apt-key add -

# BMPx
deb http://files.beep-media-player.org/packages/ubuntu dapper main universe
deb-src http://files.beep-media-player.org/packages/ubuntu dapper main universe
# -------
# wget http://files.beep-media-player.org/packages/bmp-packages.pubkey; sudo apt-key add bmp-packages.pubkey

# Cinelerra
# deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./
# deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/ ./
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./
# deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./
# deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/ ./
deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./

# debian.wgdd.de Ubuntu Repository (GPG key: E394D996)
deb http://debian.wgdd.de/ubuntu dapper universe
deb-src http://debian.wgdd.de/ubuntu dapper universe

# Quinn's Compiz
deb http://www.beerorkid.com/compiz/ dapper main
deb-src http://www.beerorkid.com/compiz/ dapper main
# -------
# wget http://ubuntu.compiz.net/quinn.key.asc -O - | sudo apt-key add -

# Compiztools
deb http://compiztools.free.fr/debian unstable main

# Easycam packages
deb http://blognux.free.fr/debian unstable main

# Ekiga & Debian pkg-voip
deb http://snapshots.seconix.com/ubuntu/ dapper main
deb http://pkg-voip.buildserver.net/ubuntu dapper main
deb-src http://snapshots.seconix.com/ubuntu/ dapper main
deb-src http://pkg-voip.buildserver.net/ubuntu dapper main
# -------
# wget http://snapshots.ekiga.net/cvs/gpgkey/buildd.gpg; sudo apt-key add buildd.gpg

# InitNG
deb http://debian.space-based.de/debs/ experimental main
deb-src http://debian.space-based.de/debs/ experimental main

# Jahshaka
deb http://repo.jahshaka.org/ubuntu/dapper binary-i386/

# Listen
deb http://theli.free.fr/packages/ dapper listen
deb-src http://theli.free.fr/packages/ dapper listen

# Lives
deb http://people.ubuntubrasil.org/~rclbelem/lives/dapper/ binary/

# Mjpegtools
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./

# MythTV
deb http://home.eng.iastate.edu/~superm1 dapper main
deb-src http://home.eng.iastate.edu/~superm1 dapper main

# NTFS-3G & Fuse
deb http://flomertens.keo.in/ubuntu/ dapper main
deb-src http://flomertens.keo.in/ubuntu/ dapper main
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ dapper main
deb-src http://ntfs-3g.sitesweetsite.info/ubuntu/ dapper main

# OpenOffice.org
deb http://people.ubuntu.com/~doko/OOo2/ ./
deb-src http://people.ubuntu.com/~doko/OOo2/ ./

# Opera
deb http://deb.opera.com/opera etch non-free

# Picard (GPG: 92132F7B)
deb http://users.musicbrainz.org/~luks/ubuntu dapper main
deb-src http://users.musicbrainz.org/~luks/ubuntu dapper main

# Samba
deb http://www.linux2go.dk/ubuntu dapper main
deb-src http://www.linux2go.dk/ubuntu dapper main

# Sinhala
deb http://sinhala.sourceforge.net/debian/i386/dapper/ ./

# Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free
# -------
# wget http://www.skype.com/download/skype/linux/rpm-public-key.asc; sudo apt-key add rpm-public-key.asc

# Suspend2 repository
#deb http://dagobah.ucc.asn.au/ubuntu-suspend2 dapper/
#deb-src http://dagobah.ucc.asn.au/ubuntu-suspend2 dapper/

# Tvfreeplayer Packages
deb http://www.tvfreeplayer.com/linux/ubuntu/dapper/ unstable main

# VLC nightlies (GPG: 81CACA84)
deb http://nightlies.videolan.org/build/dapper-i386 /
deb-src http://nightlies.videolan.org/build/dapper-i386 /

# Wine
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

# Doomsday (GPG: 4B6E7209)
deb http://eyagi.bpa.nu/~jamie/ubuntu dapper main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu dapper main restricted universe multiverse

# Spring
deb ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /
deb-src ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /

# -------------------------------------------------------------------------------------------------
# gpg --keyserver subkeys.pgp.net --recv <KEY>; gpg --export --armor <KEY> | sudo apt-key add -
```

edit: Commented out some extremely experimental repos. Added Debian stable and some other stuff.
edit2: It's even bigger now! Added a bunch of repos.

---

### Post by Uncle Spellbinder on 2006-08-27
> **ubuntu_demon said:**
> You don't need seperate repositories for opera and openoffice.org

opera is included in dapper-commercial.
Your openoffice.org repository has an older version than the one in Dapper.

Thanks!  Corrected. :wink:

---

### Post by Uncle Spellbinder on 2006-08-30
My updated sources.list -

```
##################
##### UBUNTU #####
##################

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse


#####################
##### Canonical #####
#####################

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


################################
##### Debuntu Dapper Drake #####
################################
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse


###############
##### PLF #####
###############

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free


##################
##### Amarok #####
##################

deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main
deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main


################################
##### AIGLX Compiz (Quinn) #####
################################

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb-src [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx

#deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx
#deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx

#deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx
#deb-src [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx

#deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx
#deb-src [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx


##################
##### Listen #####
##################

deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen
deb-src [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen


#####################
##### Automatix #####
#####################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
```

---

### Post by ubuntu_demon on 2006-08-31
> **Uncle Spellbinder said:**
> My updated sources.list -

```
##################
##### UBUNTU #####
##################

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse


#####################
##### Canonical #####
#####################

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


################################
##### Debuntu Dapper Drake #####
################################
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse


###############
##### PLF #####
###############

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free


##################
##### Amarok #####
##################

deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main
deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main


################################
##### AIGLX Compiz (Quinn) #####
################################

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb-src [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx

#deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx
#deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx

#deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx
#deb-src [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx

#deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx
#deb-src [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx


##################
##### Listen #####
##################

deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen
deb-src [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen


#####################
##### Automatix #####
#####################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
```
PLF is shutting down so IMHO you shouldn't use this repository.

It's better to use at little non-official repositories as possible. It's better to be conservative. You should only add repositories which you trust.

---

### Post by missmoondog on 2006-08-31
how is anyone supposed to know which repo list to use with all these on here? i just used the ones posted by uncle spellbinder and had several packages get updated that the list posted by ubuntu_demon don't touch. i should add that the ones i just updated are ones that EVERYONE would want updated also. ;)

---

### Post by Uncle Spellbinder on 2006-08-31
> **ubuntu_demon said:**
> PLF is shutting down so IMHO you shouldn't use this repository.

It's better to use at little non-official repositories as possible. It's better to be conservative. You should only add repositories which you trust.

Thanks. I did not know PLF was shutting down. Deleted PLF from my list.

---

### Post by ubuntu_demon on 2006-08-31
> **missmoondog said:**
> how is anyone supposed to know which repo list to use with all these on here? i just used the ones posted by uncle spellbinder and had several packages get updated that the list posted by ubuntu_demon don't touch. i should add that the ones i just updated are ones that EVERYONE would want updated also. ;)
Only use the ones you trust.

If you are very conservative then only trust the official Ubuntu and Canonical repositories. 

IMHO if you are running a server (for a business) then you shouldn't even use universe,multiverse or backports unless it's necessary.

I'm a bit less conservative then that since I also include skype and wine repositories in "my recommended Dapper sources.list" although uncommented :

my recommended Dapper sources.list
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by ubuntu_demon on 2006-08-31
> **Uncle Spellbinder said:**
> Thanks. I did not know PLF was shutting down. Deleted PLF from my list.
no problem :)

The news has been on their website for a while now :
[http://plf.zarb.org/](http://plf.zarb.org/)

---

### Post by missmoondog on 2006-08-31
was going to edit my above post, but since you already replied, i'll just quick reply. i'm fairly new at this linux stuff, so how do i know which ones to trust? i do look over what i'm installing and usually only install just what i need, as all of the updates needed using uncle spellbinders repos were for things i already have installed.

i do not run a server, btw.

---

### Post by ubuntu_demon on 2006-08-31
I wasn't familiar with debuntu.org repository. 

gaim 2.0 is in development. AFAIK it's in alpha or beta. So I don't know how stable it is. But I wouldn't recommend replacing gaim 1.5x which is currently in Dapper (and which is stable) with gaim 2.0.

gaim 2.0x is in the debuntu repository and if you upgrade your system you will get your gaim 1.5.x replaced by it (unless you have plugins installed which depend on gaim 1.5.x such as gaim-irchelper,gaim-extendedprefs then it probably will not upgrade gaim at all).

So I'm not going to recommend this repository for average desktop users at least for now.

This doesn't mean that I am against using the repository when you are a power user(if this repository can be trusted). I just recommend for average desktop users to keep using gaim1.5 in Dapper or wait for Edgy (gaim2.0x is in Edgy already).

You might try to request a gaim backport. More information here :[http://www.ubuntuforums.org/showthread.php?t=40291](http://www.ubuntuforums.org/showthread.php?t=40291) (although backport requests should be done using launchpad now)

**(editted a little)**

---

### Post by ubuntu_demon on 2006-08-31
> **missmoondog said:**
> was going to edit my above post, but since you already replied, i'll just quick reply. i'm fairly new at this linux stuff, so how do i know which ones to trust? i do look over what i'm installing and usually only install just what i need, as all of the updates needed using uncle spellbinders repos were for things i already have installed.


People tend to have no problems with the repositories which I recommend.

But use as little non-official repositories as possible. 

For example only use the skype repository if you need skype.

I have seen and helped people who used non-official repositories without knowing what they were doing and breaking their system by it (I don't mean their hardware ofcourse). You **might** have no problems at all until you dist-upgrade to the next Ubuntu release. I have written a guide to solve problems with broken dependencies :

HOWTO fix problems regarding broken dependencies
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

> 
If your upgrade went wrong you have to fix problems regarding package management first.

It can be very frustrating to handle broken dependencies and/or problems with apt-get/aptitude.

Possible causes :
-You started dist-upgrading while not having commented non-official Ubuntu repositories
-For some reason you had broken dependencies in Breezy, you didn't notice it and it got worse due to upgrading to Dapper
-Your system became unresponsive while dist-upgrading and you had to reboot after a while waiting.
-You have used too many unofficial repositories or bad ones.


Here is some information aimed at new users :

READ THIS FIRST from absolute beginners
[http://www.ubuntuforums.org/showthread.php?t=232059](http://www.ubuntuforums.org/showthread.php?t=232059)

This one resembles projects like ubuntuguide and Easy Ubuntu but focuses more on educating the user (I need to provide more links to relevant information) :

Ubuntu Customization Guide
[http://www.ubuntuforums.org/forumdisplay.php?f=159](http://www.ubuntuforums.org/forumdisplay.php?f=159)

> **missmoondog said:**
> 
i do not run a server, btw.

If you would run a server then you would need be extra careful/conservative.

---

### Post by missmoondog on 2006-09-10
man, i'd been afraid to use this list because of the warning that's given and from ubuntu_demon's advice. got brave just now and tried it. this definitely will give you a huge, badass sources.list!! updated just about everything on my system. i thought i was up to date using the "regular" list. 144 packages just now. that was just updating the already installed stuff. will edit and add this list to my other 6 systems.

thanks




> **HAARP said:**
> Sorry, I've posted in the discussion thread before discovering this. Delete my posts in the discussion thread please.

-original post-
If anyone wants a huge badass sources.list, use mine. 
**[size=16][color=#FF0000]USE IT WITH EXTREME CAUTION[/color][/size]**
Don't add everything at once. **New user shouldn't use this under any circumstance!** It'll give you plenty of upgradable packages, many of them you **won't** **WANT** to upgrade! **USE WITH CAUTION!**

```
# Ubuntu supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# Ubuntu community supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
# Ubuntu backports project (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

# kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main
deb http://kubuntu.org/packages/koffice-latest dapper main
deb http://kubuntu.org/packages/amarok-latest dapper main
deb-src http://kubuntu.org/packages/kde-latest dapper main
deb-src http://kubuntu.org/packages/koffice-latest dapper main
deb-src http://kubuntu.org/packages/amarok-latest dapper main

# Ubuntu commercial packages
deb http://archive.canonical.com/ubuntu dapper-commercial main
deb-src http://archive.canonical.com/ubuntu dapper-commercial main

# Kubuntu Germany
deb http://archive.czessi.net/ubuntu dapper main restricted universe multiverse preview
deb-src http://archive.czessi.net/ubuntu dapper main restricted universe multiverse preview
# -------
# wget http://archive.czessi.net/ubuntu/kczessi.gpg
# sudo apt-key add kczessi.gpg

# Ubuntu Lite
deb http://blueeyedcreature.net/ubuntu ./

# Debuntu packages
deb http://repository.debuntu.org/ dapper multiverse
deb-src http://repository.debuntu.org/ dapper multiverse
# -------
# wget http://repository.debuntu.org/GPG-Key-chantra.txt
# sudo apt-key add GPG-Key-chantra.txt

# Ubuntu Taiwan extra repository
deb http://apt.ubuntu.org.tw ubtw/
deb http://apt.ubuntu.org.tw ubtw-testing/
deb-src http://apt.ubuntu.org.tw ubtw/
deb-src http://apt.ubuntu.org.tw ubtw-testing/

# Ubuntu Dapper University Klagenfurt
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu-desktop
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu-intern
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu-nfsv4
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu-vserver
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu-testing
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu-desktop
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu-intern
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu-nfsv4
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu-vserver
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu-testing
# -------
# wget http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub
# sudo apt-key add uniklu-debuild.pub

# Penguin Liberation Front
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free

# Bazaar-NG development (GPG key: 1F44842D)
deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./
deb-src http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# A little too quiet
deb http://apt.alittletooquiet.net/staging dapper main
deb-src http://apt.alittletooquiet.net/staging dapper main

# Asher256's packages
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french
deb-src http://asher256-repository.tuxfamily.org dapper main dupdate french
deb-src http://asher256-repository.tuxfamily.org ubuntu main dupdate french

# Cafuego's packages (GPG key: 969F3F57)
deb http://ubuntu.cafuego.net/ dapper-cafuego all bcm43xx
deb-src http://ubuntu.cafuego.net/ dapper-cafuego all bcm43xx

# Doc.Horn's packages
deb http://ubuntu.moshen.de dapper all
deb-src http://ubuntu.moshen.de dapper all
# -------
# wget http://ubuntu.moshen.de/2F306651.gpg -O- | sudo apt-key add -

# Gauvain's repository
deb http://gauvain.tuxfamily.org/repos dapper contrib
deb-src http://gauvain.tuxfamily.org/repos dapper contrib

# lprod packages
deb http://lprod.org/deb/dapper/ ./
deb-src http://lprod.org/deb/dapper/ ./

# MaXeR's repository (GPG key: 35A92053)
deb http://repos.knio.it/ breezy main contrib non-free
deb-src http://repos.knio.it/ breezy main contrib non-free

# Mlind's packages (GPG key: D0AFFF5E937215FF)
deb http://www.elisanet.fi/mlind/ubuntu dapper main
deb-src http://www.elisanet.fi/mlind/ubuntu dapper main

# seb128's repository
deb http://people.ubuntu.com/~seb128/deb ./
deb-src http://people.ubuntu.com/~seb128/deb ./

# Seveas' packages (GPG key: 1135D466)
deb http://seveas.theplayboymansion.net/seveas dapper-seveas all
deb-src http://seveas.theplayboymansion.net/seveas dapper-seveas all

# Thomas' packages
deb http://thomas.enix.org/pub/debian/packages/ dapper main
deb-src http://thomas.enix.org/pub/debian/packages/ dapper main
# !!

# Treviño's repository (GPG key: 81836EBF)
deb http://3v1n0.tuxfamily.org dapper 3v1n0
deb-src http://3v1n0.tuxfamily.org dapper 3v1n0
# -------
# wget http://3v1n0.tuxfamily.org/81836EBF.gpg -O- | sudo apt-key add -

# Audacious
deb http://vdlinux.sourceforge.jp/ experimental audacious
deb-src http://vdlinux.sourceforge.jp/ experimental audacious

# Automatix
deb http://www.beerorkid.com/automatix/apt dapper main
# -------
# wget http://www.beerorkid.com/automatix/apt/key.gpg.asc
# sudo apt-key add key.gpg.asc

# BMPx
deb http://files.beep-media-player.org/packages/ubuntu dapper main universe
deb-src http://files.beep-media-player.org/packages/ubuntu dapper main universe
# -------
# wget http://files.beep-media-player.org/packages/bmp-packages.pubkey
# sudo apt-key add bmp-packages.pubkey

# Cinelerra
# deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./
# deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/ ./
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./
# deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./
# deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/ ./
deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./

# Quinn's Compiz
deb http://www.beerorkid.com/compiz/ dapper main
deb-src http://www.beerorkid.com/compiz/ dapper main
# -------
# wget http://ubuntu.compiz.net/quinn.key.asc -O - | sudo apt-key add -

# Compiztools
deb http://compiztools.free.fr/debian unstable main

# Ekiga & Debian pkg-voip
deb http://snapshots.seconix.com/ubuntu/ dapper main
deb http://pkg-voip.buildserver.net/ubuntu dapper main
deb-src http://snapshots.seconix.com/ubuntu/ dapper main
deb-src http://pkg-voip.buildserver.net/ubuntu dapper main
# -------
# wget http://snapshots.ekiga.net/cvs/gpgkey/buildd.gpg
# sudo apt-key add buildd.gpg

# InitNG
deb http://debian.space-based.de/debs/ experimental main
deb-src http://debian.space-based.de/debs/ experimental main
# !!

# Jahshaka
deb http://repo.jahshaka.org/ubuntu/dapper binary-i386/

# Listen
deb http://theli.free.fr/packages/ dapper listen
deb-src http://theli.free.fr/packages/ dapper listen

# Lives
deb http://people.ubuntubrasil.org/~rclbelem/lives/dapper/ binary/

# Mjpegtools
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./

# MythTV
deb http://home.eng.iastate.edu/~superm1 dapper main
deb-src http://home.eng.iastate.edu/~superm1 dapper main

# NTFS-3G & Fuse
deb http://flomertens.keo.in/ubuntu/ dapper main
deb-src http://flomertens.keo.in/ubuntu/ dapper main
# !!

# OpenOffice.org
deb http://people.ubuntu.com/~doko/OOo2/ ./
deb-src http://people.ubuntu.com/~doko/OOo2/ ./

# Opera
deb http://deb.opera.com/opera etch non-free

# Samba
deb http://www.linux2go.dk/ubuntu dapper main
deb-src http://www.linux2go.dk/ubuntu dapper main
# !!

# Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Suspend2 repository
deb http://dagobah.ucc.asn.au/ubuntu-suspend2 dapper/
deb-src http://dagobah.ucc.asn.au/ubuntu-suspend2 dapper/
# !!

# VLC (GPG key: 81CACA84)
deb http://nightlies.videolan.org/build/dapper-i386 /
deb-src http://nightlies.videolan.org/build/dapper-i386 /

# Wine
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main
# !!

# Doomsday Engine (GPG key: 4B6E7209)
deb http://eyagi.bpa.nu/~jamie/ubuntu dapper main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu dapper main restricted universe multiverse

# Spring
deb ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /
deb-src ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /

# ----------------------------------------------------------------------------------
# gpg --keyserver subkeys.pgp.net --recv <KEY>
# gpg --export --armor <KEY> | sudo apt-key add -

```

---

### Post by ubuntu_demon on 2006-09-13
> **missmoondog said:**
> man, i'd been afraid to use this list because of the warning that's given and from ubuntu_demon's advice. got brave just now and tried it. this definitely will give you a huge, badass sources.list!! updated just about everything on my system. i thought i was up to date using the "regular" list. 144 packages just now. that was just updating the already installed stuff. will edit and add this list to my other 6 systems.

thanks

You might be lucky and notice no breakage during Dapper but get unlucky during the dist-upgrade to Edgy and have a broken system. Seriously you should be conservative or be willing to encounter some breakage.

Also do you trust the owners of these unofficial repositories ? If you just randomly add some repositories you aren't very much better of than a windows user who has to browse the internet and download and install exe files to get some things working.

Ofcourse everyone should make their own informed choices. If you decide to trust these unofficial repositories it's your own right to do so :).

---

### Post by arsenic23 on 2006-09-13
Hmmm, seems like a lot of decent advice being thrown around here. 

My sources are a bit out of date, I haven't touched them since I first installed dapper and started hunting around for repos I needed to get a few things working.  Anyone know other repos I could use to get the newest version of Comix ?

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse


# Opera & Picard
deb http://deb.opera.com/opera/ unstable non-free
deb http://users.musicbrainz.org/~luks/ubuntu dapper main

# XGL
deb http://xgl.compiz.info/ dapper main

# Wine
deb http://wine.sourceforge.net/apt binary/
deb-src http://wine.sourceforge.net/apt source/

# For Newer Comix
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

## http 100mbit/s mirror provided thanks to OVH (http://ovh.com)
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

```

---

### Post by HAARP on 2006-09-16
> **missmoondog said:**
> man, i'd been afraid to use this list because of the warning that's given and from ubuntu_demon's advice. got brave just now and tried it. this definitely will give you a huge, badass sources.list!! updated just about everything on my system. i thought i was up to date using the "regular" list. 144 packages just now. that was just updating the already installed stuff. will edit and add this list to my other 6 systems.

thanks

Nice to hear someone using it :)
I've updated the list. Changelog: Commented out some extremely experimental repos, added Debian stable and some other stuff
-> 22750 packages :)
You still will want to use some pinning.

Thanks ubuntu-demon, I've added the security issues to the warnings.

edit: A few more changes. Added information on what to do if apt runs out of space
-> 22935 packages

---

### Post by ubuntu_demon on 2006-09-16
> **HAARP said:**
> 
Thanks ubuntu-demon, I've added the security issues to the warnings.

You are welcome. I urge everyone to be as conservative as possible. Especially if you can't risk major breakage.

---

### Post by HAARP on 2006-10-02
Just an update to let you know I've updated my huge sources.list again. A bunch of repositores have been added, including experimental ones. Those are commented out! If you really dare to use them, remove their #'s

- 440 repos
- 23038 packages
- 1 crazy idiot

---

### Post by frogotronic on 2006-11-26
here's my small list - works well.

I've got a Broadcom Wireless PCMCIA card.

The BiBUS program is an open source replacement for EndNote that works really well with OpenOffice writer.

```
## Main Restricted Dapper Drake Repository
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

## Main Restricted Dapper Drake Security Updates
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

## Universe Dapper Drake Security Updates
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

## Broadcom 43xx WiFi PCMCIA Card Driver Repository
deb http://ubuntu.cafuego.net dapper-cafuego bcm43xx
deb-src http://ubuntu.cafuego.net dapper-cafuego bcm43xx

## BiBUS Bibliography Programme Repository
deb http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./
deb-src http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./


## Automatix Repository
deb http://www.getautomatix.com/apt dapper main


#AUTOMATIX REPOS START

deb http://people.ubuntu.com/~seb128/deb ./

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
#AUTOMATIX REPOS END
```

Good Luck

-CH

---

