---
title: "Whats your sources.list?"
date: 2006-06-28
forum: The Cafe
---

### Post by codypumper on 2006-06-28
I still have the fresh install sources.list. Just curious what other users were using.

---

### Post by christofer.c.bell on 2006-06-28
I've simplified the default and split out any respository beyond those enabled by the stock list into [FONT="Courier New"]/etc/apt/sources.list.d[/FONT].  So this is what I have for [FONT="Courier New"]/etc/apt/sources.list[/FONT]:

> [FONT="Courier New"]# Ubuntu 6.06 LTS (Canonical Ltd. Support)
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
[/FONT]

In [FONT="Courier New"]/etc/apt/sources.list.d[/FONT], I have the following files:

> [FONT="Courier New"]cbell@demeter:/etc/apt/sources.list.d$ ls
freenx.list               plf.list.disabled
multiverse.list.disabled  universe.list.disabled
[email]cbell@demeter:/etc/apt/sources.list[/email].d$
[/FONT]

These files contain the following:
[FONT="Courier New"]
***freenx.list***
> # Seveas mirror for the freenx software.  For more information on Seveas and
# freenx, please refer to the following information: 
#
#    [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX) and 
#    [https://wiki.ubuntu.com/SeveasPackages](https://wiki.ubuntu.com/SeveasPackages)
#
# The homepage for the Seveas project is:
#
#    [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/)
#
# To install gpg keys for this repository, run the following commands:
#
#	$ gpg --keyserver subkeys.pgp.net --recv-keys 1135D466
#	$ gpg --export --armor 1135D466 | sudo apt-key add -
#

deb [http://mirror2.ubuntulinux.nl/](http://mirror2.ubuntulinux.nl/) dapper-seveas freenx
deb-src [http://mirror2.ubuntulinux.nl/](http://mirror2.ubuntulinux.nl/) dapper-seveas freenx

***multiverse.list.disabled***
> # Ubuntu Multiverse (Community Support)
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security multiverse

***plf.list.disabled***
> # Penguin Liberation Front Repository
# 
# PLF is a packaging project dedicated to distributing software that 
# cannot be included in Linux distributions for various reasons:
# 
#     * software patents, prohibiting the use of abtract algorithms 
#       regardless of implementation
# 
#     * corporate interest protection laws, such as DMCA in USA, and EUCD 
#       soon in Europa
# 
#     * privacy restriction laws, such as strong cryptography prohibition 
#       in many countries
# 
# A lot of excellent free software falls under one of these different 
# threats, and thus becomes illegal in various parts of the world. This 
# actually restricts their distribution worlwide, making their use at 
# least impractical, if not impossible, unless for experts. We don't 
# resign to this situation however, and we provide first-class packages 
# for all these endangered software. Wherever you are, there is always a 
# PLF mirror near.

# The homepage of this repository can be found at [http://plf.zarb.org/](http://plf.zarb.org/)
  
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

***universe.list.disabled***
> # Ubuntu Universe (Community Support)
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
[/FONT]

Since the files in [FONT="Courier New"]/etc/apt/sources.list.d[/FONT] are only read if they end in the [FONT="Courier New"].list[/FONT] extention, I can easily enable and disable non-default repositories by renaming the files.

Sure, it's perhap a bit anal, but it seems more elegant to me than what comes with the system. :)

---

### Post by aysiu on 2006-06-28
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by John.Michael.Kane on 2006-06-28
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)[/QUOTE]

Same.....

---

### Post by user1397 on 2006-06-29
[quote=SD-Plissken]Same.....[/quote]same.....

---

### Post by yaztromo on 2006-06-29
I've tried to tidy the default one up a bit and make it more readable.

> 
#Main
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

#Post release bug fix updates
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

#Backports
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

#Security updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

#KDE 3.5.3
deb [http://kubuntu.org/packages/kde-353](http://kubuntu.org/packages/kde-353) dapper main

#Rarewares
#deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./


---

### Post by hardfire_avk on 2006-06-29
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)[/QUOTE]

Same but with lot's of Error's. God Knows Why?

---

### Post by ubuntu_demon on 2006-06-29
**my recommended Dapper sources.list**
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
## only uncomment it if you need it
## deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
## deb-src ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

## Dapper PLF
## only uncomment it if you need it
## deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
## deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
## deb http://wine.budgetdedicated.com/apt dapper main
## deb-src http://wine.budgetdedicated.com/apt dapper main

## skype 
## only uncomment it if you need it
## deb http://download.skype.com/linux/repos/debian/ stable non-free

```

---

### Post by NESFreak on 2006-06-29
check out [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) so you can make your own in just a few simple clicks.

---

### Post by GarethMB on 2006-06-29
Same as Aysiu's plus:

deb [http://kubuntu.org/packages/amarok-14](http://kubuntu.org/packages/amarok-14) dapper main

---

### Post by halfvolle melk on 2006-06-29
Pretty much the same as all the above but I commented out all the "deb-src".

---

### Post by ubuntu_demon on 2006-06-30
I created a poll right here :

What are your favorite non-official repositories for Dapper?
[http://www.ubuntuforums.org/showthread.php?p=1198291](http://www.ubuntuforums.org/showthread.php?p=1198291)

---

### Post by .t. on 2006-06-30
My sources.list:
```
#Ubuntu
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

#Listen
deb http://theli.free.fr/packages/dapper/ ./

#Non-FOSS software
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

#amaroK latest
deb http://kubuntu.org/packages/amarok-latest dapper main

#WINE
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

#AIGLX/Compiz
deb http://xgl.compiz.info/ dapper main aiglx
deb-src http://xgl.compiz.info/ dapper main aiglx

#Debian (see apt-preferences)
deb     http://ftp.uk.debian.org/debian unstable main contrib non-free
deb-src http://ftp.uk.debian.org/debian unstable main contrib non-free

#InitNG (broken)
#deb http://debian.space-based.de/debs/ experimental main
#deb-src http://debian.space-based.de/debs/ experimental main

#Cinelerra (broken)
#deb ftp://ftp.nerim.net/debian-marillat/ sid main
#deb http://www.kiberpipa.org/~gandalf/ubuntu/breezy/mjpegtools ./
#deb http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/i686/ ./
```

---

### Post by picpak on 2006-06-30
```
# Ubuntu 6.06 LTS (Canonical Ltd. Support)
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## Cipherfunk multimedia packages
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

## Dapper PLF
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

## Wine
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

## Skype 
#deb http://download.skype.com/linux/repos/debian/ stable non-free

## Opera
deb http://deb.opera.com/opera/ unstable non-free

## Sylpheed-Claws
deb http://claws.sylpheed.org/ubuntu/dapper/ ./

## Audacity
deb http://morgoth.free.fr/ubuntu dapper-backports main

## Gauvain Pocentek's repository
deb http://gauvain.tuxfamily.org/repos dapper contrib
deb-src http://gauvain.tuxfamily.org/repos dapper contrib

## Java 1.5.0+update07, updated w32codecs
deb http://ubuntu.geole.de/ dapper universe multiverse

## Seveas
deb http://mirror3.ubuntulinux.nl dapper-seveas all
deb-src http://mirror3.ubuntulinux.nl dapper-seveas all

## Automatix
# deb http://www.getautomatix.com/apt dapper main
```

---

