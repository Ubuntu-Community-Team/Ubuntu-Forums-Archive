---
title: "Ubuntu Sources List Generator : 'dangerous' or not ??"
date: 2010-01-15
forum: The Cafe
---

### Post by newbie2 on 2010-01-15
[Ubuntu Sources List Generator]("http://repogen.simplylinux.ch/") , the ['alternative' to source-o-matic]("https://answers.launchpad.net/ubuntu-nl-website/+question/22521") is it a 'dangerous' tool or a 'safe' tool for newbies to use ?? Because on the internet, there are several sites that 'promote' this tool : 
[http://www.google.com/search?cf=all&ned=us&hl=en&q=ubuntu+sources+list+generator&btnmeta%3Dsearch%3Dsearch=Search+the+Web](http://www.google.com/search?cf=all&ned=us&hl=en&q=ubuntu+sources+list+generator&btnmeta%3Dsearch%3Dsearch=Search+the+Web)
:confused::rolleyes::-k

---

### Post by wojox on 2010-01-15
I've tried it out before. It's fine. ;)

---

### Post by newbie2 on 2010-01-15
By 'dangerous' i meant here : could it not be used with malicious repositories/code from some 'hackers' who want 'more' than to help you...:rolleyes:

---

### Post by wojox on 2010-01-15
That's all it looks like.

```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ karmic main 
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main 
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main 
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main 
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Cairo Dock - http://www.cairo-dock.org/ww_page.php?p=Accueil&#9001;=en
## Run this command: wget -q http://repository.cairo-dock.org/cairo-dock.gpg -O- | sudo apt-key add -
deb http://repository.cairo-dock.org/ubuntu karmic cairo-dock

#### Chromium Project - http://code.google.com/chromium/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 4E5E17B5 && gpg --export --armor 4E5E17B5 | sudo apt-key add -
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

#### Conky - https://launchpad.net/conky
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 95628707
deb http://ppa.launchpad.net/norsetto/ppa/ubuntu karmic main

#### Mozilla Daily Build Team - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
## Run this command: gpg --keyserver subkeys.pgp.net --recv-key 247510BE && gpg --armor --export  247510BE | sudo apt-key add -
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main


####### 3rd Party Source Repos

#### Chromium Project (Source) - http://code.google.com/chromium/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 4E5E17B5 && gpg --export --armor 4E5E17B5 | sudo apt-key add -
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

#### Conky (Source) - https://launchpad.net/conky
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 95628707
deb-src http://ppa.launchpad.net/norsetto/ppa/ubuntu karmic main

#### Mozilla Daily Build Team (Source) - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
## Run this command: gpg --keyserver subkeys.pgp.net --recv-key 247510BE && gpg --armor --export  247510BE | sudo apt-key add -
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main


```

I don't think there are any 'hackers' hanging around there.

---

### Post by newbie2 on 2010-01-15
There are some on the Dutch Ubuntu forum that do not trust it though :
[http://forum.ubuntu-nl.org/documentatie/ubuntu-sources-list-generator/](http://forum.ubuntu-nl.org/documentatie/ubuntu-sources-list-generator/)
:rolleyes:

---

### Post by doas777 on 2010-01-15
and remember the automatix2 thing. everyone loved it until the ubuntu devs cracked it open and realized that it was just not good for a system (not malicious, just not a good idea either).

---

### Post by Xbehave on 2010-01-15
this just generates a sources.lst, it does everything by the book (well by the apt technically), so it seams fine the only potential problem is that users are going to be trusting 3rd party repos. Perhaps 
> considered as trusted - those repos are considered as trusted by my. This does not mean they can't/won't harm your system. I consider them as good however you use them on your own risk.  should be bigger but on the whole i think it's good

---

### Post by slakkie on 2010-01-15
> **newbie2 said:**
> There are some on the Dutch Ubuntu forum that do not trust it though :
[http://forum.ubuntu-nl.org/documentatie/ubuntu-sources-list-generator/](http://forum.ubuntu-nl.org/documentatie/ubuntu-sources-list-generator/)
:rolleyes:

The reasons he uses are not that convincing. I agree with the think before you act attitude which he has. But other then that. It is not SUPER DUPER dangerous, like he says. He adds something of irritating to support, the man is a bit too paranoid.

---

### Post by Uncle Spellbinder on 2010-01-15
I've used it several times. Generated what I needed for my soiurces.list then added PPA's and getdeb. Never had an issue. 

```
############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Karmic CD ROM
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


###### Ubuntu Karmic Main
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse

###### Ubuntu Karmic Update
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse

###### Ubuntu Karmic Security
deb http://security.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse

###### Ubuntu Karmic Backports
deb http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

###### Ubuntu Partner
deb http://archive.canonical.com/ubuntu karmic partner



##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

#### Chromium Project
## gpg --keyserver subkeys.pgp.net --recv 4E5E17B5 && gpg --export --armor 4E5E17B5 | sudo apt-key add -
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

#### GetDeb
## wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
deb http://archive.getdeb.net/ubuntu karmic-getdeb apps

#### Medibuntu
## sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb http://packages.medibuntu.org/ karmic free non-free

#### Miro HD Video Player
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu karmic/

#### Ubuntuzilla
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
## To install, use the following in terminal:
## sudo apt-get install firefox-mozilla-build
## sudo apt-get install thunderbird-mozilla-build
## sudo apt-get install seamonkey-mozilla-build



##############################################################
###################### LAUNCHPAD PPA's #######################
##############################################################

#### Abiword 
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2382D57E
deb http://ppa.launchpad.net/abiword-stable/ubuntu karmic main

#### Aurora Gtk2 Engine 
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0AAFAD78
deb http://ppa.launchpad.net/merlwiz79/aurora/ubuntu karmic main

#### Avant Window Navigator (AWN Testing Team - Trunk Builds)
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com BF810CD5
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu karmic main

#### Exaile
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 43CBFCC0
deb http://ppa.launchpad.net/exaile-devel/ppa/ubuntu karmic main

#### Nvidia Vdpau Team PPA
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main

#### MediaInfo
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9D8BC54
deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu karmic main

#### Quod Libet (Trunk Builds)
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5806C7C4
deb http://ppa.launchpad.net/lazka/dumpingplace/ubuntu karmic main

#### Themes for GNOME and Ubuntu
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main 

#### Ubuntu Tweak
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu karmic main

#### Virtual Box
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 62F1201A
deb http://ppa.launchpad.net/debfx/virtualbox/ubuntu karmic main
```

---

