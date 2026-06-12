---
title: "my recommended breezy sources.list(discussion)"
date: 2005-11-09
forum: Repositories &amp; Backports
---

### Post by ubuntu_demon on 2005-11-09
This is the discussion thread for this sticky :

[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

Sometimes people post also their own sources.list here. Don't let that confuse you.

---

### Post by Dutch on 2005-11-09
But ... I have Ubuntu 5.04 Hoary Hedhoge.
Can I then also use this list ? ore am I in trouble now ?

---

### Post by Dutch on 2005-11-09
My source list after upgrading to Breeze 


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## Officials Backports
## arent't available yet
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-extras main universe multiverse restricted

## backports-extras 
## freenx will be available here
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

## [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [ftp://antesis.freecontrib.org/freecontrib/mirrors/ubuntu/plf/](ftp://antesis.freecontrib.org/freecontrib/mirrors/ubuntu/plf/) breezy free non-free
deb-src [ftp://antesis.freecontrib.org/freecontrib/mirrors/ubuntu/plf/](ftp://antesis.freecontrib.org/freecontrib/mirrors/ubuntu/plf/) breezy free non-free

---

### Post by ubuntu_demon on 2005-11-09
This is a breezy sources.list.

upgrading instructions from hoary to breezy are found here :
[https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)

I'll help you on IM.

---

### Post by siimo on 2005-11-11
mine is like this:

```

#breezy
deb http://mirror.optus.net/ubuntu/ breezy main restricted universe multiverse
#breezy-security
deb http://mirror.optus.net/ubuntu/ breezy-security main restricted universe multiverse
#breezy-updates
deb http://mirror.optus.net/ubuntu/ breezy-updates main restricted universe multiverse
#breezy-backports
deb http://mirror.optus.net/ubuntu/ breezy-backports main restricted universe multiverse
#plf
deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free
```

---

### Post by bored2k on 2005-11-11
```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

---

### Post by DoeRayMe on 2005-11-11
[QUOTE=bored2k]```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```[/QUOTE]

maybe a stupid question but whats the difference between using 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

or

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-security universe?

---

### Post by Kvark on 2005-11-11
why?
```
deb http://se.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://se.archive.ubuntu.com/ubuntu breezy main restricted

deb http://se.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://se.archive.ubuntu.com/ubuntu breezy universe
deb-src http://se.archive.ubuntu.com/ubuntu breezy universe

deb http://se.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

---

### Post by rattaro on 2005-11-11
Sorry I can't post mine yet, since I'm not home, but I wanted to ask something that I'm reminded of.  What's the difference between a source and binary repository?  I know that one has sources, and the other has binaries, but why have both?  When you apt-get something from the src repository, does your computer compile it, and install it?  Or do some programs/libraries need to be installed as the source code?  What gives?

---

### Post by PatrickMay16 on 2005-11-11
> 
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


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

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## RareWares/Debian Multi-Media Repository for Unstable
deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/


Also, I would like to take the opportunity to say that **Phil Collins** is a cool guy.

---

### Post by manicka on 2005-11-11
```
## Uncomment the following two lines to fetch updated software from the network
deb-src http://au.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
deb-src http://au.archive.ubuntu.com/ubuntu breezy universe

deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://wine.sourceforge.net/apt binary/
#deb-src http://wine.sourceforge.net/apt source/

## mirror provided thanks to OVH http://ovh.com
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
#deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted

deb http://people.ubuntu.com/~doko/OOo2 ./
```

---

### Post by ubuntu_demon on 2005-11-11
```

deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

#plf
deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

```

My sources.list is also found here : [http://www.ubuntuforums.org/showthread.php?t=87946](http://www.ubuntuforums.org/showthread.php?t=87946)

edit: plf mirror found thnx to slimo!

---

### Post by siimo on 2005-11-11
Just wanted to see if you guys have any cool repositores other than the standard ones. All i've found is PLF so far that has stuff like w32codecs and realplayer.  as you can see i'm new :rolleyes:

---

### Post by siimo on 2005-11-11
[QUOTE=ubuntu_demon]

I commented plf because the repo seems down and I don't want people to get "strange" errors.
[/QUOTE]

check my first post I found a nice stable mirror for that PLF repo

---

### Post by siimo on 2005-11-11
[QUOTE=rattaro]Sorry I can't post mine yet, since I'm not home, but I wanted to ask something that I'm reminded of.  What's the difference between a source and binary repository?  I know that one has sources, and the other has binaries, but why have both?  When you apt-get something from the src repository, does your computer compile it, and install it?  Or do some programs/libraries need to be installed as the source code?  What gives?[/QUOTE]
it is there if you want to get the source packages and change something and compile yourself.

Backport developers also use these src repos to grab source packages from currentversion+1 and compile it on currentversion

e.g. from dapper -> breezy  

This makes it much easier than packaging the deb from scratch.

---

### Post by ubuntu_demon on 2005-11-11
[QUOTE=siimo]check my first post I found a nice stable mirror for that PLF repo[/QUOTE]
cool thnx!

---

### Post by Bairsairk on 2005-11-11
```
#OpenOffice 2.0 final, not beta like ubuntu repos
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

#aMule cvs build with de-centralized network
deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
```

---

### Post by rattaro on 2005-11-12
[QUOTE=siimo]it is there if you want to get the source packages and change something and compile yourself.

Backport developers also use these src repos to grab source packages from currentversion+1 and compile it on currentversion

e.g. from dapper -> breezy  

This makes it much easier than packaging the deb from scratch.[/QUOTE]


That makes sense.  I thought so but really wasn't sure.  Thanks for the info!

---

### Post by Kvark on 2005-11-12
[QUOTE=siimo]it is there if you want to get the source packages and change something and compile yourself.

Backport developers also use these src repos to grab source packages from currentversion+1 and compile it on currentversion

e.g. from dapper -> breezy  

This makes it much easier than packaging the deb from scratch.[/QUOTE]
So if you're not going to change something and compile yourself then you don't need the src repos?

---

### Post by DoeRayMe on 2005-11-12
yep thats right ^

---

### Post by `GooZ´ on 2005-11-13
[QUOTE=Bairsairk]```
#OpenOffice 2.0 final, not beta like ubuntu repos
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

#aMule cvs build with de-centralized network
deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
```[/QUOTE]
Thx for the tip! Now running OOo final :-)

---

### Post by defcon on 2005-11-13
```
deb http://de.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://de.archive.ubuntu.com/ubuntu breezy universe multiverse main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

##Backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging restricted

```

---

### Post by stubby on 2005-11-13
cheers

this should be plastered all over ubuntuforums so that people know which sources list to use.

---

### Post by Stormy Eyes on 2005-11-13
```
deb http://ubuntupc.com/ubuntu public-sources/

deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse
```

Yeah, I'm hardcore. :)

---

### Post by `GooZ´ on 2005-11-13
@ Stormy Eyes:
deb [http://ubuntupc.com/ubuntu](http://ubuntupc.com/ubuntu) public-sources/
What's this one for?

---

### Post by Stormy Eyes on 2005-11-13
[QUOTE=`GooZ´]@ Stormy Eyes:
deb [http://ubuntupc.com/ubuntu](http://ubuntupc.com/ubuntu) public-sources/
What's this one for?[/QUOTE]

I got my computer from [Open Sense Solutions](http://ubuntupc.com/). Their installation of Ubuntu includes their own repository. I've had the machine since June and it's been purring like a kitten.

---

### Post by `GooZ´ on 2005-11-13
Looks very nice! Especially the SLIM would be very nice to use at work (in multiple cubicles) or so...

---

### Post by Stormy Eyes on 2005-11-13
[QUOTE=`GooZ´]Looks very nice! Especially the SLIM would be very nice to use at work (in multiple cubicles) or so...[/QUOTE]

Their prices are pretty reasonable, too. I use the Lini, since I just needed a machine for myself and wanted Ubuntu instead of Debian. (I don't think I'm hardcore enough to install pure Debian, even though I've installed and run Gentoo.)

---

### Post by `GooZ´ on 2005-11-13
Looks very nice indeed, especially for only $600, which is approx €510! Think I'm going to consider one too ;-)

---

### Post by Stormy Eyes on 2005-11-13
[QUOTE=`GooZ´]Looks very nice indeed, especially for only $600, which is approx €510! Think I'm going to consider one too ;-)[/QUOTE]

You might want to toss 'em an email and see if they ship internationally; international shipping does tend to cost a metric arseload, even for little things like CDs. I would know; I married a girl from Australia after a four-year long-distance relationship.

---

### Post by `GooZ´ on 2005-11-13
[QUOTE=Stormy Eyes]I would know; I married a girl from Australia after a four-year long-distance relationship.[/QUOTE]
Hehe, OK. Enough for the off-topic now ;-)

---

### Post by jdong on 2005-11-13
[QUOTE=Stormy Eyes]I got my computer from [Open Sense Solutions](http://ubuntupc.com/). Their installation of Ubuntu includes their own repository. I've had the machine since June and it's been purring like a kitten.[/QUOTE]
aah, they have their own kernel packages (probably not security maintained) and aren't releasing sources (GPL violation)!

You might wanna talk to them about the GPL breach at least, and perhaps switch to a Ubuntu kernel....

---

### Post by tbrownaw on 2005-11-13
```
# See sources.list(5) for more information, especialy
# Remember that you can only use http, ftp or file URIs
# CDROMs are managed through the apt-cdrom tool.

#Extra packages

#deb ftp://ftp.crosswire.org/pub/sword/packages/debian woody main

deb http://quozl.netrek.org/pptp/pptpconfig ./

#Mplayer
#deb ftp://ftp.nerim.net/debian-marillat/ stable main
#deb ftp://ftp.nerim.net/debian-marillat/ testing main
#deb ftp://ftp.nerim.net/debian-marillat/ unstable main

#Ubuntu
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse

#Standard Debian package distribution

#deb http://http.us.debian.org/debian unstable main contrib non-free
#deb http://non-us.debian.org/debian-non-US unstable/non-US main contrib non-free
#deb-src http://http.us.debian.org/debian unstable main contrib non-free
#deb-src http://non-us.debian.org/debian-non-US unstable/non-US main contrib non-free

#deb http://http.us.debian.org/debian testing main contrib non-free
#deb http://non-us.debian.org/debian-non-US testing/non-US main contrib non-free
#deb-src http://http.us.debian.org/debian testing main contrib non-free
#deb-src http://non-us.debian.org/debian-non-US testing/non-US main contrib non-free

```

...I never actually installed Ubuntu, just "upgraded" to it from Debian.

---

### Post by Stormy Eyes on 2005-11-13
[QUOTE=jdong]You might wanna talk to them about the GPL breach at least, and perhaps switch to a Ubuntu kernel....[/QUOTE]

I am *so* not getting involved with GPL issues, **jdong**. It's none of my business whether or not Open Sense adheres to the GPL.

---

### Post by ubuntu_demon on 2005-11-16
[QUOTE=stubby]cheers

this should be plastered all over ubuntuforums so that people know which sources list to use.[/QUOTE]
I stickied it

---

### Post by rkelly on 2005-11-18
[quote=ubuntu_demon]I stickied it[/quote] Are you sure?

---

### Post by ubuntu_demon on 2005-11-18
Now this is the discussion thread for this sticky :

[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by GothicX on 2005-11-24
What's the difference between deb and deb-src ?! deb-src is for files like tcl8.4-dev !? and backports needs a line for deb-src ?

deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse

Something like that...

---

### Post by ubuntu_demon on 2005-11-25
[QUOTE=GothicX]What's the difference between deb and deb-src ?! deb-src is for files like tcl8.4-dev !? and backports needs a line for deb-src ?

deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse

Something like that...[/QUOTE]
deb-src is for source packages. With the source you can compile a pakacage yourself. For example sometimes it is needed to compile your kernel yourself to make it work with some exotic hardware.

---

### Post by Remmelas on 2005-11-25
[QUOTE=Stormy Eyes]I am *so* not getting involved with GPL issues, **jdong**. It's none of my business whether or not Open Sense adheres to the GPL.[/QUOTE]

Anyway, i'm not sure which sources they 'aren't releasing' but looks like they've got them up on the web for whoever wants them  [http://ubuntupc.com/ubuntu/public-sources/](http://ubuntupc.com/ubuntu/public-sources/)

---

### Post by Vlammend on 2005-11-26
When I add the universe repositories, including the security updates, a lot of updates are listed. But I get the idea that some versions will be turned backwards:

sources after adding Universe:
```


deb http://nl.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://nl.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nl.archive.ubuntu.com/ubuntu breezy universe
deb-src http://nl.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

After loading synaptic wants to update the following:
```
gnome-gv (versie 1:2.8.4-0ubuntu2) zal bijgewerkt worden naar versie 1:2.12.0-0ubuntu1
gtkhtml3.6 (versie 3.6.2-0ubuntu1) zal bijgewerkt worden naar versie 3.6.2-1
lesstif2 (versie 1:0.93.94-11ubuntu3) zal bijgewerkt worden naar versie 1:0.93.94-11.4ubuntu3
libgal2.4-0 (versie 2.4.1-0ubuntu1) zal bijgewerkt worden naar versie 2.5.3-0ubuntu1
libgal2.4-common (versie 2.4.1-0ubuntu1) zal bijgewerkt worden naar versie 2.5.3-0ubuntu1
libgtkhtml3.6-18 (versie 3.6.2-0ubuntu1) zal bijgewerkt worden naar versie 3.6.2-1
openoffice.org (versie 1.1.3-8ubuntu2) zal bijgewerkt worden naar versie 1.1.5-0ubuntu1
openoffice.org-bin (versie 1.1.3-8ubuntu2-1) zal bijgewerkt worden naar versie 1.1.5-0ubuntu1-0ubuntu1
openoffice.org-gtk-gnome (versie 1.1.3-8ubuntu2-1) zal bijgewerkt worden naar versie 1.1.5-0ubuntu1-0ubuntu1
openoffice.org-help-en (versie 1.1+20040420-2ubuntu1) zal bijgewerkt worden naar versie 1.1+20040420-3
openoffice.org-l10n-en (versie 1.1.3-8ubuntu2) zal bijgewerkt worden naar versie 1.1.5-0ubuntu1
openoffice.org-l10n-nl (versie 1.1.3-8ubuntu2.3) zal bijgewerkt worden naar versie 1.1.5-0ubuntu1
xpdf (versie 3.00-11ubuntu3) zal bijgewerkt worden naar versie 3.01-1ubuntu1
xpdf-common (versie 3.00-11ubuntu3) zal bijgewerkt worden naar versie 3.01-1ubuntu1
xpdf-reader (versie 3.00-11ubuntu3) zal bijgewerkt worden naar versie 3.01-1ubuntu1
xpdf-utils (versie 3.00-11ubuntu3) zal bijgewerkt worden naar versie 3.01-1ubuntu1
lesstif1 (versie 1:0.93.94-11.4ubuntu3) zal geïnstalleerd worden
openoffice.org1-debian-files (versie 1.1.5-0+1ubuntu1) zal geïnstalleerd worden
```

sorry that it is in dutch, but the idea is clear I think. Now which is newer:
x.x.x-ubuntu3 or x.x.x+-ubuntu1??
:confused:

---

### Post by ubuntu_demon on 2005-11-26
Vlammend : you have to look at the entire version number instead of just the last part.

For example : 1.0.3-ubuntu1 is newer than 1.0.1-ubuntu3

---

### Post by Limulus on 2005-12-06
I just [found out]("http://ubuntuforums.org/showthread.php?p=550722") from jdong, who founded and runs the [backports]("http://ubuntuforums.org/showthread.php?t=40291"), that extras has basically been all but scrapped, with a lot of its functionality being taken over by the PLF.  I have thus removed extras from my sources.list and would recommend the same for the stickied list.

---

### Post by ubuntu_demon on 2005-12-07
[QUOTE=Limulus]I just [found out]("http://ubuntuforums.org/showthread.php?p=550722") from jdong, who founded and runs the [backports]("http://ubuntuforums.org/showthread.php?t=40291"), that extras has basically been all but scrapped, with a lot of its functionality being taken over by the PLF.  I have thus removed extras from my sources.list and would recommend the same for the stickied list.[/QUOTE]

thnx. I removed the repo since there aren't any packages in it.

---

### Post by gil-galad on 2005-12-08
[QUOTE=Remmelas]Anyway, i'm not sure which sources they 'aren't releasing' but looks like they've got them up on the web for whoever wants them  [http://ubuntupc.com/ubuntu/public-sources/](http://ubuntupc.com/ubuntu/public-sources/)[/QUOTE]

Looks fine.  Jdong, *please* do not accuse people of anything without any evidence.  And the gpl only states that they have to provide the sources to their customers (The people having the software distributed to them).  Unless you have bought a pc from them and they have refused to give you the source, do not accuse them of breaking the gpl.

Anyway, this is my first post in awhile.

---

### Post by mschievano on 2005-12-11
```

#usual
deb http://it.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

#Extras
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main
deb http://ubuntu-backports.mirrormax.net/ breezy-extras restricted
deb http://ubuntu-backports.mirrormax.net/ breezy-extras universe
deb http://ubuntu-backports.mirrormax.net/ breezy-extras multiverse

#wine
deb http://wine.sourceforge.net/apt/ binary/

#kde
deb http://kubuntu.org/packages/kde35 breezy main

#openoffice
deb http://people.ubuntu.com/~doko/OOo2 ./
deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free
deb http://apt.bxlug.be ooo/ # packages additionels pour openoffice

#opera browser
deb http://deb.opera.com/opera/ etch non-free

#Amarok
deb http://kubuntu.org/packages/amarok-1.3.7 breezy main

#Doomsday games
deb http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse

#Freenx
deb http://seveas.ubuntulinux.nl/ breezy-seveas all
deb-src http://seveas.ubuntulinux.nl/ breezy-seveas all


```

very hard!

---

### Post by Limulus on 2005-12-12
mschievano: Just a few questions...

Why do you have both Breezy and Dapper repositories?

Why do you have "deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse" and not "deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main universe multiverse restricted"?

What is the Kubuntu repository needed for?

Why do you have PLF under 'Open Office'?

Also, FYI, Breezy Extras have been pretty much scrapped: [http://ubuntuforums.org/showthread.php?p=550722](http://ubuntuforums.org/showthread.php?p=550722)

---

### Post by hl2u on 2005-12-12
sorry for the noobish question, but when opening 
synaptic, after typing my passw. i'am getting this 
warning :

```


W: Nu pot determina starea listei surse de pachete [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-amd64_Packages) - stat (2 No such file or directory)



```

i mention that i use breezy 5.1 on amd 64 and the above warning appeared 
after installing and using "automatix".

thanks in advance for any clue .

---

### Post by ubuntu_demon on 2005-12-12
[QUOTE=hl2u]sorry for the noobish question, but when opening 
synaptic, after typing my passw. i'am getting this 
warning :

"W: Nu pot determina starea listei surse de pachete [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
"

i mention that i use breezy 5.1 on amd 64 and the above warning appeared 
after installing and using "automatix".

thanks in advance for any clue .[/QUOTE]

automatix probably messed up your sources.list somehow. Try changing to my sources.list. Instructions are here : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by hl2u on 2005-12-12
thanks for your fast answer but... it didn't help.
the same error warning keep comming  even after copy/paste
your sources from the quoted thread + restarting the X

---

### Post by ubuntu_demon on 2005-12-12
You have to make sure there are no typo's in the corresponding sources.list entries.

And you have to type :
$ sudo apt-get update

---

### Post by h.mehdi on 2005-12-12
when I do `sudo apt-get update' and it starts updating I see lines starting with `Ign' & `Hit' & `get' ...
Can any one please tell me what does these `Ign' & `Hit' & `get' means ?

Thanks

---

### Post by Limulus on 2005-12-12
[QUOTE=hl2u]thanks for your fast answer but... it didn't help.
the same error warning keep comming  even after copy/paste
your sources from the quoted thread + restarting the X[/QUOTE]
In Synaptic, try pressing Reload...  Does that make the errors go away?

---

### Post by ubuntu_demon on 2005-12-13
[QUOTE=h.mehdi]when I do `sudo apt-get update' and it starts updating I see lines starting with `Ign' & `Hit' & `get' ...
Can any one please tell me what does these `Ign' & `Hit' & `get' means ?

Thanks[/QUOTE]
that's just normal output of what is happening. It's not an error.

---

### Post by mschievano on 2005-12-13
[QUOTE=Limulus]mschievano: Just a few questions...

Why do you have both Breezy and Dapper repositories?

Why do you have "deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse" and not "deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main universe multiverse restricted"?

What is the Kubuntu repository needed for?

Why do you have PLF under 'Open Office'?

Also, FYI, Breezy Extras have been pretty much scrapped: [http://ubuntuforums.org/showthread.php?p=550722](http://ubuntuforums.org/showthread.php?p=550722)[/QUOTE]

1. Breezy to mantain some packages to the stable version
2. Dapper for the contrary
3. I've added the main and restricted packages
4. Kubuntu because i use k3b instead of gnomebaker
5. I change the position for PLF
6. I have deleted some repos

My new sources:

```

#standard 5.10
deb http://it.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu   breezy-security main restricted universe multiverse

#Extras 5.10
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main
deb http://ubuntu-backports.mirrormax.net/ breezy-extras restricted
deb http://ubuntu-backports.mirrormax.net/ breezy-extras universe
deb http://ubuntu-backports.mirrormax.net/ breezy-extras multiverse

#dapper 6.04
deb http://it.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse 

#other applications

#wine
deb http://wine.sourceforge.net/apt/ binary/

#kde
deb http://kubuntu.org/packages/kde35 breezy main

#openoffice
deb http://people.ubuntu.com/~doko/OOo2 ./
deb http://apt.bxlug.be ooo/ # packages additionels pour openoffice

#PLF
deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

#opera browser
deb http://deb.opera.com/opera/ etch non-free

#Amarok
deb http://kubuntu.org/packages/amarok-1.3.7 breezy main

#Doomsday games
deb http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse

```

---

### Post by hl2u on 2005-12-13
And my saga goes on :(    :

-copy/paste your sources, **ubuntu_demon** :
and 

```


me@mymachine:~$ sudo apt-get update
Ignorat [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Luat:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Luat:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Luat:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ignorat [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
Ignorat [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Ignorat [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Ignorat [http://deb.opera.com](http://deb.opera.com) etch Release
Luat:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Atins [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ignorat [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Ignorat [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Ignorat [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Atins [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ignorat [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ignorat [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Ignorat [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Ignorat [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Atins [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Atins [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Eroarehttp://packages.freecontrib.org breezy/free Packages
  404 Not Found
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Eroarehttp://deb.opera.com etch/non-free Packages
  404 Not Found
Eroarehttp://packages.freecontrib.org breezy/non-free Packages
  404 Not Found
Atins [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Atins [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Ignorat [http://public.planetmirror.com](http://public.planetmirror.com) breezy Release.gpg
Luat:5 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Atins [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Atins [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Atins [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Atins [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Atins [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Atins [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Atins [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Ignorat [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Luat:6 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Ignorat [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Luat:7 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Ignorat [http://public.planetmirror.com](http://public.planetmirror.com) breezy Release
Ignorat [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Luat:8 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Ignorat [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages
Ignorat [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Luat:9 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Ignorat [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages
Ignorat [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Luat:10 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Eroarehttp://public.planetmirror.com breezy/free Packages
  404 Not Found [IP: 203.16.234.19 80]
Ignorat [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Luat:11 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Eroarehttp://public.planetmirror.com breezy/non-free Packages
  404 Not Found [IP: 203.16.234.19 80]
Eroareftp://ftp.free.fr breezy/free Packages
  Nu pot aduce fi&#351;ierul, serverul a spus 'Failed to open file.
Luat:12 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Eroareftp://ftp.free.fr breezy/non-free Packages
  Nu pot aduce fi&#351;ierul, serverul a spus 'Failed to open file.
Atins [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Atins [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Adus 4B &#238;n 5s (1B/s)
E&#351;uare &#238;n aducerea [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz)  404 Not Found
E&#351;uare &#238;n aducerea [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz)  404 Not Found
E&#351;uare &#238;n aducerea [http://deb.opera.com/opera/dists/etch/non-free/binary-amd64/Packages.gz](http://deb.opera.com/opera/dists/etch/non-free/binary-amd64/Packages.gz)  404 Not Found
E&#351;uare &#238;n aducerea [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz)  Nu pot aduce fi&#351;ierul, serverul a spus 'Failed to open file.
E&#351;uare &#238;n aducerea [http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz)  404 Not Found [IP: 203.16.234.19 80]
E&#351;uare &#238;n aducerea [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz)  Nu pot aduce fi&#351;ierul, serverul a spus 'Failed to open file.
E&#351;uare &#238;n aducerea [http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz)  404 Not Found [IP: 203.16.234.19 80]
E: Nu pot determina blocajul /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mama@mama:~$ sudo apt-get upgrade
E: Nu pot determina blocajul /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
me@mymachine:~$


```


**Limulus**, "reload" in synaptic :

```


"http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz: 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:) 404 Not Found
[http://deb.opera.com/opera/dists/etch/non-free/binary-amd64/Packages.gz:](http://deb.opera.com/opera/dists/etch/non-free/binary-amd64/Packages.gz:) 404 Not Found
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz:) Nu pot aduce fi&#351;ierul, serverul a spus 'Failed to open file.
[http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz:](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz:) 404 Not Found [IP: 203.16.234.91 80]
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:) Nu pot aduce fi&#351;ierul, serverul a spus 'Failed to open file.
[http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:) 404 Not Found [IP: 203.16.234.91 80]


```

+

```


W: Nu pot determina starea listei surse de pachete [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-amd64_Packages) - stat (2 No such file or directory)


```

Any ideas, please ?

---

### Post by Limulus on 2005-12-13
[QUOTE=mschievano]Kubuntu because i use k3b instead of gnomebaker[/quote]

I use K3B too, so I tried adding *deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main*, but it didn't offer me a new version of K3B.  Note that its not mentioned in [http://kubuntu.org/packages/kde35/dists/breezy/main/binary-i386/Packages](http://kubuntu.org/packages/kde35/dists/breezy/main/binary-i386/Packages)

(the most recent version seems to be 0.12.7-1ubuntu1~breezy1 from breezy-backports)

[QUOTE=mschievano]
My new sources:

[snip]
```

#Extras 5.10
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main
deb http://ubuntu-backports.mirrormax.net/ breezy-extras restricted
deb http://ubuntu-backports.mirrormax.net/ breezy-extras universe
deb http://ubuntu-backports.mirrormax.net/ breezy-extras multiverse
```[/QUOTE]

As per [http://ubuntuforums.org/showthread.php?p=550722](http://ubuntuforums.org/showthread.php?p=550722) the guy who runs backports (and extras) said "Breezy Extras is empty, and if at all possible I intend on keeping it that way."

---

### Post by Limulus on 2005-12-13
> **hl2u]And my saga goes on :(

[snip]

**Limulus**, "reload" in synaptic :

"http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz: 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:) 404 Not Found
[http://deb.opera.com/opera/dists/etch/non-free/binary-amd64/Packages.gz:](http://deb.opera.com/opera/dists/etch/non-free/binary-amd64/Packages.gz:) 404 Not Found
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz:) Nu pot aduce fi&#351 said:**
> http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz:[/url] 404 Not Found [IP: 203.16.234.91 80]
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:) Nu pot aduce fi&#351;ierul, serverul a spus 'Failed to open file.
[http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:) 404 Not Found [IP: 203.16.234.91 80]
"

+

"

W: Nu pot determina starea listei surse de pachete [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-amd64_Packages) - stat (2 No such file or directory)

"

Any ideas, please ?
A closer look at the errors you're getting reveals that you're using an AMD64 processor, aren't you?  This is a problem because many of the repositories don't carry binaries for it.

Remove the PLF and Opera repositories and your errors should clear up...

---

### Post by hl2u on 2005-12-13
"Remove the PLF and Opera repositories and your errors should clear up..."

cool, it did help indeed, thank you !!  But... if I want to upgrade some applications- let's say Open Office or Firefox ( even those multimedia codecs ) - for my AMD 64 , what I'm supose to add to my sources list ?

---

### Post by Limulus on 2005-12-13
[QUOTE=hl2u]"Remove the PLF and Opera repositories and your errors should clear up..."

cool, it did help indeed, thank you !!  But... if I want to upgrade some applications- let's say Open Office or Firefox ( even those multimedia codecs ) - for my AMD 64 , what I'm supose to add to my sources list ?[/QUOTE]

All the **Official** Ubuntu Repositories support AMD64, so you don't need to worry about getting the right packages as far as those go (e.g. Firefox).  Its only when you want to expand beyond them that you have to be aware of what the repositories contain.

An example: The official repositories contain OpenOffice.org2 version *1.9* (which is to say, a beta of version 2.0). ubuntu_demon's repository for version 2.0 is:

```
## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./
```

But if you used that (BTW, to enable a repository you have to remove the #'s in front of lines which start with "deb") it would **not** work for you since you have an AMD64 processor...  Instead, the line you would have to use is:

```
deb http://people.ubuntu.com/~doko/OOo2-amd64/ ./
```

(ubuntu_demon: note also that the correct repository for PPC is *deb [http://people.ubuntu.com/~doko/OOo2-powerpc/](http://people.ubuntu.com/~doko/OOo2-powerpc/) ./* )

BTW, once you've installed OO.o 2.0, you can remove that line, since the next version will most likely end up in Backports.

As far as proprietary codecs go, that's more tricky; see for example [http://www.ubuntuforums.org/showthread.php?t=62685](http://www.ubuntuforums.org/showthread.php?t=62685)

---

### Post by Limulus on 2005-12-13
ubuntu_demon: two things...

First, since your list is the one "which I recommend for the average desktop user running breezy", why do you have all the deb-src entries?  Average users will never compile packages from source and it takes longer to download the repository info ;)

Second, I thought you might want to include the repository:

```
deb http://pkg-boinc.alioth.debian.org/ubuntu breezy universe
```
to get Boinc (used for Seti@home, etc.).

See [http://ubuntuforums.org/showthread.php?t=99584](http://ubuntuforums.org/showthread.php?t=99584)
and [http://ubuntuforums.org/showthread.php?t=96930](http://ubuntuforums.org/showthread.php?t=96930)

---

### Post by ubuntu_demon on 2005-12-13
Thnx for the input guys! I editted my sticky.

The average desktop user has no ppc or amd64.

It can't hurt to include the src repos in case you might need them later. If you are on a slow internet connection I would advise to remove them.

IMHO the people who need boinc will find the repo on the forums.(most average desktop users won't need boinc) I don't want to complicate the sources.list too much.

---

### Post by ubuntu_demon on 2006-01-02
information about apt-get :

[http://www.ubuntuforums.org/showthread.php?t=103462](http://www.ubuntuforums.org/showthread.php?t=103462)

---

### Post by bonzodog on 2006-01-03
I have just discovered that amd64 support isn't included, and you say extras is no longer used? So is what *do* amd64 users get? Can someone post an *up to date* sources.list for amd64? I still have the extras enabled in my sources.list as I found out that the plf repos do not support 64 bit.

---

### Post by Limulus on 2006-01-06
> **bonzodog]I have just discovered that amd64 support isn't included, and you say extras is no longer used? So is what *do* amd64 users get? Can someone post an *up to date* sources.list for amd64? I still have the extras enabled in my sources.list as I found out that the plf repos do not support 64 bit.[/QUOTE]

There's no point to having extras in your sources.list if you have Breezy because its empty said:**
> http://ubuntuforums.org/showpost.php?p=550792&postcount=43[/url]

You're also unfortunately not the first person to notice the lack of packages compiled for AMD64: [http://ubuntuforums.org/showpost.php?p=609647&postcount=234](http://ubuntuforums.org/showpost.php?p=609647&postcount=234)

Basically, what someone with AMD64 can get (easily) is the basic Ubuntu Install plus OpenOffice.org 2.0; AFAIK, there are no prepared packages for  AMD64 Opera, nor Boinc and in order to get w32codecs, you'll need a 32 bit media player which is a extra work to install properly.  You can also compile some packages for yourself from source, but that still doesn't help with things like Opera.

If you're ok with that, then use a sources.list like this:

[quote]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-security main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main universe multiverse restricted
deb [http://people.ubuntu.com/~doko/OOo2-amd64](http://people.ubuntu.com/~doko/OOo2-amd64) ./
If not, you might seriously want to consider installing the i386 version of Ubuntu...  Hope that helps, not that its good news :/

In the long run though, support for AMD64 should improve.

---

### Post by lysis on 2006-01-09
[QUOTE=Stormy Eyes]You might want to toss 'em an email and see if they ship internationally; international shipping does tend to cost a metric arseload, even for little things like CDs. I would know; I married a girl from Australia after a four-year long-distance relationship.[/QUOTE]


she got any friends?  :p

---

### Post by lysis on 2006-01-09
[QUOTE=mschievano]```

#usual
deb http://it.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

#Extras
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main
deb http://ubuntu-backports.mirrormax.net/ breezy-extras restricted
deb http://ubuntu-backports.mirrormax.net/ breezy-extras universe
deb http://ubuntu-backports.mirrormax.net/ breezy-extras multiverse

#wine
deb http://wine.sourceforge.net/apt/ binary/

#kde
deb http://kubuntu.org/packages/kde35 breezy main

#openoffice
deb http://people.ubuntu.com/~doko/OOo2 ./
deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free
deb http://apt.bxlug.be ooo/ # packages additionels pour openoffice

#opera browser
deb http://deb.opera.com/opera/ etch non-free

#Amarok
deb http://kubuntu.org/packages/amarok-1.3.7 breezy main

#Doomsday games
deb http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse

#Freenx
deb http://seveas.ubuntulinux.nl/ breezy-seveas all
deb-src http://seveas.ubuntulinux.nl/ breezy-seveas all


```

very hard![/QUOTE]




i want to use these, but a lot of them "can't verify keys"

---

### Post by Limulus on 2006-01-10
[QUOTE=lysis]i want to use these, but a lot of them "can't verify keys"[/QUOTE]
You should still be able to install them, even without the keys... (you'll just get a warning message first).  I don't know if all of them even have keys, but the key for the KDE packages (for Amarok, KDE and Koffice) is on [http://kubuntu.org/announcements/amarok-1.3.7.php](http://kubuntu.org/announcements/amarok-1.3.7.php) (or see the other announcements)

BTW, I was looking at these two:

#kde
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main
#Amarok
deb [http://kubuntu.org/packages/amarok-1.3.7](http://kubuntu.org/packages/amarok-1.3.7) breezy main

If you go to [http://kubuntu.org/packages/](http://kubuntu.org/packages/) you'll note that there exists subdirectories "amarok-latest" and "kde-latest" which have the exact same timestamp as the ones you quoted with version numbers; thus to keep as up to date as possible, I would suggest:

#kde
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main
#Amarok
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) breezy main

---

### Post by proxess on 2006-01-14
```
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy universe
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
deb http://wine.sourceforge.net/apt/ binary/
deb http://people.ubuntu.com/~doko/OOo2 ./
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb http://deb.opera.com/opera/ etch non-free
## deb http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
```

---

### Post by jamesstansell on 2006-01-25
> It can't hurt to include the src repos in case you might need them later. If you are on a slow internet connection I would advise to remove them.

I'm on a slow connection, but had to put my deb-src lines back in.  I tried taking them out when I upgraded from Hoary to Breezy, but synaptic (and apt in general, I think) was very confused about what packages I had and which ones I wanted.  I tried repeatedly to make it work without the deb-src lines, but finally putting them back in made everything work.  I should clarify that I wasn't using anything but the binary packages.

I haven't messed with it since then.  Whenever I try to run without the src repos again, I will post about whatever I discover.

-james.

---

### Post by Limulus on 2006-01-25
[QUOTE=jamesstansell]I'm on a slow connection, but had to put my deb-src lines back in.  I tried taking them out when I upgraded from Hoary to Breezy, but synaptic (and apt in general, I think) was very confused about what packages I had and which ones I wanted.  I tried repeatedly to make it work without the deb-src lines, but finally putting them back in made everything work.  I should clarify that I wasn't using anything but the binary packages.

I haven't messed with it since then.  Whenever I try to run without the src repos again, I will post about whatever I discover.[/QUOTE]
Synaptic will give me an error if I start it after altering my sources.list file because the changes are new to it; I can fix that by either (a) ignoring the error for the moment and pressing the reload button which then makes it go away for future uses, or (b) running *sudo apt-get update* after changing the sources.list but before running Synaptic.

If you feel like doing a little experiment, edit your sources list (sudo gedit /etc/apt/sources.list) and instead of removing the deb-src entries, put a # in front of them.  The # character at the beginning of a line tells apt/synaptic to ignore that line.  Then run *sudo apt-get update* and then try Synaptic.  Any errors?

---

### Post by Gowator on 2006-01-30
What sources am I meant or best adding to use the libpimp stuff in Dapper so I can use musicbrainz etc?  I read deb unstable works ... ?

---

### Post by Cesium on 2006-02-19
I changed my sources.list based off this sources.list.  I was having problems with synaptic since I think a site for a repository was down, but now no longer have problems so thanks for the sources.list.  

What effects are there from using this sources.list instead of what I already had?

---

### Post by Mishal on 2006-02-20
Can anyone direct me to a link where I can LEARN how the whole system of repos work? :)

I want to know which repo keeps what type of packages and how keys work etc etc.

---

### Post by ubuntu_demon on 2006-02-21
[QUOTE=Mishal]Can anyone direct me to a link where I can LEARN how the whole system of repos work? :)

I want to know which repo keeps what type of packages and how keys work etc etc.[/QUOTE]
Here are a lot of links :
[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by ubuntu_demon on 2006-04-07
[QUOTE=ubuntu_demon]Here are a lot of links :
[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)[/QUOTE]

I added the Cipherfunk repo for its multimedia packages.

---

### Post by Peetke on 2006-05-04
You can use the following Wine mirror (much faster than SourceForge):
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt)  breezy main
deb-src [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main

(and switch breezy for dapper if you're running dapper)

See the wine newsletter for more info:
[http://www.winehq.com/?issue=310#New%20apt%20Repository](http://www.winehq.com/?issue=310#New%20apt%20Repository)

---

### Post by ubuntu_demon on 2006-05-05
[QUOTE=Peetke]You can use the following Wine mirror (much faster than SourceForge):
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt)  breezy main
deb-src [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main

(and switch breezy for dapper if you're running dapper)

See the wine newsletter for more info:
[http://www.winehq.com/?issue=310#New%20apt%20Repository](http://www.winehq.com/?issue=310#New%20apt%20Repository)[/QUOTE]
cool thnx!

---

