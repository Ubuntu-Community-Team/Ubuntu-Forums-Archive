---
title: "[Edgy]Ubuntu Customization Quick Guide - WORK IN PROGRESS"
date: 2006-10-21
forum: Ubuntu Customization Guide
---

### Post by ubuntu_demon on 2006-10-21
** this is a work in progress. This is on your own risk. This is not aimed at businesses or servers. This is aimed at regular desktop/laptop users**

**linux-generic :**
This will get you the generic kernel including restricted modules :
$sudo aptitude install linux-generic

**my recommended edgy sources.list :**
```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nl.archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

## seveas-edgy contains some nice stuff including w32codecs,libdvdcss2,flashplugin-nonfree
## with flash 9 beta and some nice meta-packages
## http://seveas.imbrandon.com
## http://seveas.imbrandon.com/dists/edgy-seveas
deb http://seveas.imbrandon.com edgy-seveas custom extras seveas-meta backports
deb-src http://seveas.imbrandon.com edgy-seveas custom extras seveas-meta backports

```

You should add the two letter country code of your country to improve your download speed such as nl,us in all lines of your sources.list like this :
```

deb http://**nl**.security.ubuntu.com/ubuntu edgy-security main restricted

```

More information about seveas repository :
[http://seveas.imbrandon.com](http://seveas.imbrandon.com)
[http://seveas.imbrandon.com/dists/edgy-seveas](http://seveas.imbrandon.com/dists/edgy-seveas)

To add seveas to your trusted sources :
```

wget http://seveas.imbrandon.com/1135D466.gpg -O- | sudo apt-key add -

```

Do not use ***all*** unless you have to because it will also contain drivers and such in the future.

**ubuntu-multimedia-gnome** :

ubuntu-multimedia-gnome
[quote=description]
    This package will install a complete multimedia system for the GNOME desktop,
    including codecs, players and catalog programs

    It is safe to remove this package again after installed, the services themself
    will not be removed with it
[/quote]
banshee, beep-media-player, gstreamer0.10-pitfdll, gstreamer0.10-plugins-bad, gstreamer0.10-plugins-bad-multiverse, gstreamer0.10-plugins-good, gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse, gtkpod, jokosher, libdvdcss2, mozilla-mplayer, mplayer, quodlibet, totem, vlc, w32codecs

You should also install flashplugin-nonfree if you want to view flash.

---

### Post by weazle on 2006-10-24
How do I import your public key ?

[I]W: GPG error: [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
[/I]

// weazle

---

### Post by ubuntu_demon on 2006-10-24
I'm not seveas ;) But I do know him personally.

```

wget http://seveas.imbrandon.com/1135D466.gpg -O- | sudo apt-key add -

```

---

### Post by weazle on 2006-10-24
Cool, it worked :-) Thanks !

---

### Post by angrykeyboarder on 2006-10-28
> **ubuntu_demon said:**
> I'm not seveas ;) But I do know him personally.

```

wget [http://seveas.imbrandon.com/1135D466.gpg](http://seveas.imbrandon.com/1135D466.gpg) -O- | sudo apt-key add -

```

I've not seen the "-O-" in that entry before.  I tried it and it just hung.

So I just downloaded the key and sudo apt-key added it.

---

### Post by FyreBrand on 2006-10-29
This is a nice beginning to the Edgy customization guide.  Thanks for starting to build it.  Also thanks to Seveas and those working with him for providing such a killer repo.

Everything has gone really smooth.

---

### Post by ember on 2006-10-31
Great work - I tend to prefer your guide over Automatix or other scripts because it leaves much more control to me. I am looking forward to see the Edgy guide grow.

---

### Post by phaedOne on 2006-11-18
lovin it :cool:

---

### Post by angrykeyboarder on 2006-11-18
I like your sources.list file.  I have all of the same links, except that I take advantage of the [many many Ubuntu Mirror servers]("https://wiki.ubuntu.com/Archive") out there. This lessens the load on Ubuntu and it can provide faster downloads.  Not to mention a lot of mirrors seem to be going to waste.

In addtion, the [PLF]("http://wiki.ubuntu-fr.org/doc/plf") has some [nice non-free Ubuntu packages]("http://wiki.ubuntu-fr.org/doc/plf#ubuntu_6.10_edgy_eft").

This is my sources.list file.:

```
## Main Archive [Mirror] - Main, Restricted, Universe and Multiverse Repositories
deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) edgy main restricted universe multiverse
deb-src [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) edgy-updates main restricted
deb-src [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) edgy-updates main restricted

## Backports
deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) edgy-backports main restricted universe multiverse

##Proposed Updates
deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) edgy-proposed universe main multiverse restricted
deb-src [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) edgy-proposed universe main multiverse restricted

##Bleeding edge wine packages (packages)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

##Swiftfox
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

##KOffice Update
deb [http://ftp.gtlib.cc.gatech.edu/pub/kde/stable/koffice-1.6.0/kubuntu](http://ftp.gtlib.cc.gatech.edu/pub/kde/stable/koffice-1.6.0/kubuntu) edgy main
#deb-src [http://ftp.gtlib.cc.gatech.edu/pub/kde/stable/koffice-1.6.0/kubuntu](http://ftp.gtlib.cc.gatech.edu/pub/kde/stable/koffice-1.6.0/kubuntu) edgy main

##Security
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe

##Canonical Commercial
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main 

##Sevas
deb [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas custom extras seveas-meta
deb-src [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas custom extras seveas-meta

##giFT FastTrack
#deb [ftp://ftp.berlios.de/pub/gift-fasttrack/](ftp://ftp.berlios.de/pub/gift-fasttrack/) unstable main
deb-src [ftp://ftp.berlios.de/pub/gift-fasttrack/](ftp://ftp.berlios.de/pub/gift-fasttrack/) unstable main

##Freevo
deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) edgy universe multiverse

##KDE Themes for Debian Sid
# deb [http://mirror.pusling.com/debian/unstable](http://mirror.pusling.com/debian/unstable) ./
# deb-src [http://mirror.pusling.com/debian/unstable](http://mirror.pusling.com/debian/unstable) ./

##Amarok 1.4.4
deb [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy main
#deb-src [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy main

##The Opera Browser (packages)
#
#gpg --keyserver subkeys.pgp.net --recv-key 6A423791
#gpg --armor --export 6A423791| apt-key add -
#
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

##Penguin Liberation Front
# deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) edgy free non-free
# deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) edgy free non-free

## PLF fallback repository - edgy
deb [http://mrpouit.free.fr/plf-fallback](http://mrpouit.free.fr/plf-fallback) edgy-plf free non-free
deb-src [http://mrpouit.free.fr/plf-fallback](http://mrpouit.free.fr/plf-fallback) edgy-plf free non-free

# BPMx CVS
deb [http://files.beep-media-player.org/packages/ubuntu](http://files.beep-media-player.org/packages/ubuntu) edgy main universe testing

# Jedit
# deb [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./
# deb-src [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./

##malteo's repository
deb [http://malteo.homelinux.net/](http://malteo.homelinux.net/) edgy-malteo all


```

---

### Post by foogod on 2006-11-23
> **angrykeyboarder said:**
> I've not seen the "-O-" in that entry before.  I tried it and it just hung.

So I just downloaded the key and sudo apt-key added it.

FYI, this is probably because you missed the "Password:" prompt that sudo printed mixed in with the output from wget.  It was waiting for you to enter your password to complete the operation.

To avoid this problem, add a -q to the wget command line:

```
wget http://seveas.imbrandon.com/1135D466.gpg -O- -q | sudo apt-key add -
```

---

### Post by P235 on 2006-12-08
Thank you for your guide, it is very helpful and much more engaging than using easyubuntu or automatix.  As a newbie, this guide was simple to apply, and answered a number of questions to a few embedded video issues as well!  I'll be giving the flash installation a try @ my next earliest convenience.  By the way, is there a list of country codes to refer to in order to increase download speed?  Thanks again!

---

### Post by Tuna on 2006-12-15
This is my first post as I've just gotten around to registering, but I've been reading and absorbing info for the last couple of weeks (being a good newbie :)).  I just want to say, your customization guide for Dapper was great, and this one is really helpful as well since I've now upgraded to Edgy.  Thanks a lot for these guides!  \\:D/

---

### Post by Pobega on 2006-12-16
> **ubuntu_demon said:**
> **ubuntu-multimedia-gnome** :

ubuntu-multimedia-gnome

banshee, beep-media-player, gstreamer0.10-pitfdll, gstreamer0.10-plugins-bad, gstreamer0.10-plugins-bad-multiverse, gstreamer0.10-plugins-good, gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse, gtkpod, jokosher, libdvdcss2, mozilla-mplayer, mplayer, quodlibet, totem, vlc, w32codecs

Maybe it's just me but ubuntu-multimedia-gnome doesn't work for me. My package manager is telling me that the package doesn't exist.

---

### Post by FyreBrand on 2006-12-16
> **Pobega said:**
> Maybe it's just me but ubuntu-multimedia-gnome doesn't work for me. My package manager is telling me that the package doesn't exist.Do you have the seveas repos enabled in your sources.list?  That is where that meta-package resides.  I just did:
```
aptitude search ubuntu-multimedia-gnome
p   ubuntu-multimedia-gnome                         - Ubuntu multimedia packages - GNOME version
```
So the package is still available.  What didn't work for you?

---

### Post by SilverE2 on 2006-12-19
This may be a stupid question...but I know I totally forgot to do it, and I couldn't figure out why it wasn't showing up for me:

Did you run apt-get update?

---

### Post by FyreBrand on 2007-02-24
Could this be cleaned up and stickied or amended to the Dapper guide?  At least ubuntu-demons first post added to the sticky list would be nice.

---

### Post by ubuntu_demon on 2007-03-26
> **FyreBrand said:**
> Could this be cleaned up and stickied or amended to the Dapper guide?  At least ubuntu-demons first post added to the sticky list would be nice.
I will try to work on it. (I'm a bit busy lately) I will definetely post a feisty guide before feisty is released.

---

### Post by FyreBrand on 2007-03-26
I'm not a guide or Linux expert but I would be willing to help.  I'm kind of busy too so I understand how hard it is to devote time or get spread thin.  If you need anything let me know.  I'm running Feisty - Kubuntu now.

This is what I've noticed that's a little different from previous versions.

The MOTU for wine keeps a fairly updated wine backport going.  The latest release is already in the repository.  No real need for a bleeding edge wine repo.

Beryl is in the repository so no need to real need to use the beryl repo either.

Real Player and Acroread are no longer in the repositories and the Canonical Commercial repo is now sketchy at best.

The only third party repo I'm using at the moment is seveas'.

Almost everything is provided by official repositories.  This is pretty good.  Anyway let me know if you want any help or want a repository source tested..

---

### Post by ubuntu_demon on 2007-03-26
> **FyreBrand said:**
> I'm not a guide or Linux expert but I would be willing to help.  I'm kind of busy too so I understand how hard it is to devote time or get spread thin.  If you need anything let me know.  I'm running Feisty - Kubuntu now.


Thanks for the offer. The best help you can give me is commenting (questions/suggestions..) on the Edgy and Feisty guides when I finish them.

> **FyreBrand said:**
> 
This is what I've noticed that's a little different from previous versions.

The MOTU for wine keeps a fairly updated wine backport going.  The latest release is already in the repository.  No real need for a bleeding edge wine repo.

Beryl is in the repository so no need to real need to use the beryl repo either.

Real Player and Acroread are no longer in the repositories and the Canonical Commercial repo is now sketchy at best.

The only third party repo I'm using at the moment is seveas'.

Almost everything is provided by official repositories.  This is pretty good.  Anyway let me know if you want any help or want a repository source tested..


In the edgy version of my guide / sources.list  seveas is my only unofficial repo.  I'm happy with the seveas repo so I will add it as a recommendation in the Dapper guide.

For the Dapper the unofficial repos in my guide are commented and I suggest only uncommenting them if you need them. I will consider removing them or making it more clear that you shouldn't uncomment them unless you need them.

wine is availabe in edgy-backports but not in dapper-backports
the version of wine availabe in dapper has a changelog with the latest entry being on "Mon, 29 May 2006 12:37:24 +0100". IMHO it could happen that some people would like the bleeding edge version of wine in Dapper.

I won't include beryl or compiz repositories in my guides. IMHO the best approach for "average desktop users" of testing compiz is by upgrading to Feisty (or installing Feisty) when it releases.

Thanks for the suggestions and input. Keep it up.

Regards,

ubuntu_demon

---

### Post by FyreBrand on 2007-03-26
This has been one of the most helpful threads to get installed and running whatever I need.  I'm glad to help.

I was mostly looking at Feisty installs rather than Dapper because you've pretty much covered the Dapper area completely.

I don't think Canonical Commercial will be the best answer for Edgy or Feisty users because the Opera package in there, last I checked, is still at 9.0.  Opera does provide a repository that seems worth using.  I tested out a few of their repositories and would recommend trying 'unstable' as it's built on Debian using GCC 4.0.  The stable and testing repositories are built on RedHat 9.0 using GCC 3.2.  I'm not sure if RedHat uses a different directory structure, but having it built on Debian might help ensure that plug-in paths are more compatible.

this is the repo: deb [http://deb.opera.com/opera](http://deb.opera.com/opera) unstable non-free

If I notice anything different I'll report back.

---

### Post by ubuntu_demon on 2007-03-26
> **FyreBrand said:**
> This has been one of the most helpful threads to get installed and running whatever I need.  I'm glad to help.

I was mostly looking at Feisty installs rather than Dapper because you've pretty much covered the Dapper area completely.

I don't think Canonical Commercial will be the best answer for Edgy or Feisty users because the Opera package in there, last I checked, is still at 9.0.  Opera does provide a repository that seems worth using.  I tested out a few of their repositories and would recommend trying 'unstable' as it's built on Debian using GCC 4.0.  The stable and testing repositories are built on RedHat 9.0 using GCC 3.2.  I'm not sure if RedHat uses a different directory structure, but having it built on Debian might help ensure that plug-in paths are more compatible.

this is the repo: deb [http://deb.opera.com/opera](http://deb.opera.com/opera) unstable non-free

If I notice anything different I'll report back.
thanks :)

---

