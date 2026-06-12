---
title: "Post your EDGY sources.list"
date: 2006-09-25
forum: Repositories &amp; Backports
---

### Post by Uncle Spellbinder on 2006-09-25
OK, so it's only nearing the end of September and the final release of Edgy Eft is a month or so away. Nevertheless, here it is. 

* **Post your EDGY sources.list here.** *

If this thread dies a sad death cuz it's "too early"..........oh well :rolleyes: 

Here's mine:
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

##### MAJOR BUG FIX UPDATES#####
##(produced after the final release)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

##### UBUNTU SECURITY UPDATES #####
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

##### BACKPORTS REPOSITORY #####
##(Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
                                                                                                                                                                          
##### CANONICAL COMMERCIAL REPOSITORY #####
##(Hosted on Canonical servers, not Ubuntu servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

##### PLF REPOSITORY #####
##(Unsupported.  May contain illegal packages.  Use at own risk.)
#deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy free non-free
#deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy free non-free

##### PLF #####
##(Please report any bug on [https://launchpad.net/products/plf/+bugs](https://launchpad.net/products/plf/+bugs))
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy-plf free non-free

##### LISTEN #####
deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen
##deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen listen-unstable
##deb-src [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen listen-unstable

##### Beryl #####
deb [http://dev.realistanew.com/beryl](http://dev.realistanew.com/beryl) edgy beryl
deb-src [http://dev.realistanew.com/beryl](http://dev.realistanew.com/beryl) edgy beryl
deb [http://beryl-mirror.lupine.me.uk/beryl](http://beryl-mirror.lupine.me.uk/beryl) edgy beryl
deb-src [http://beryl-mirror.lupine.me.uk/beryl](http://beryl-mirror.lupine.me.uk/beryl) edgy beryl
```

---

### Post by reacocard on 2006-09-25
```
##### OFFICIAL REPOS #####

## Ubuntu
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Updates
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Backports
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse


##### UNOFFICAL REPOS #####

## Fonts
deb http://www.elisanet.fi/mlind/ubuntu edgy fonts
deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts
```

Nothing fancy. All the ubuntu repos, and some repos for improving font rendering.

BTW, how well does beryl work right now with those repos?

---

### Post by Uncle Spellbinder on 2006-09-25
> **reacocard said:**
> BTW, how well does beryl work right now with those repos?

Originally I was us using Compiz Quinn AIGLX. I set Beryl up like this: [http://www.ubuntuforums.org/showpost.php?p=1543996&postcount=126](http://www.ubuntuforums.org/showpost.php?p=1543996&postcount=126)

Working flawlessly thus far.

---

### Post by reacocard on 2006-09-25
> **Uncle Spellbinder said:**
> Originally I was us using Compiz Quinn AIGLX. I set Beryl up like this: [http://www.ubuntuforums.org/showpost.php?p=1543996&postcount=126](http://www.ubuntuforums.org/showpost.php?p=1543996&postcount=126)

Working flawlessly thus far.

Thanks. Just upgraded, working beautifully so far.

---

### Post by BigWillyT on 2006-10-18
Does anyone know what's up with the repos?!?  Went home at lunch today after getting the NVIDIA drivers installed this morning and I can't find any of the beryl/emerald packages on any of the repos.  Someone please help!!!!  I gotta have my eyecandy! :)

---

### Post by Anonii on 2006-10-18
```

deb ftp://ftp.nerim.net/debian-marillat/ unstable main

deb http://gr.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gr.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

;_;
What do I win?

---

### Post by reacocard on 2006-10-18
Update of my sources.list. I've added the beryl repos, and a repo for the latest brasero (disc burner like k3b, but for gnome).

```
##### OFFICIAL REPOS #####

## Ubuntu
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Updates
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Backports
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse


##### UNOFFICAL REPOS #####

## Fonts (http://ubuntuforums.org/showthread.php?t=235526) (libcairo, libxft)
deb http://www.elisanet.fi/mlind/ubuntu edgy fonts
deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts

## Beryl (http://www.beryl-project.org)
deb http://www.beerorkid.com/compiz edgy main-edgy
deb-src http://www.beerorkid.com/compiz edgy main-edgy

## Brasero (http://mrpouit.tuxfamily.org/dists/edgy-pouit/extra/)
deb http://mrpouit.tuxfamily.org edgy-pouit extra
deb-src http://mrpouit.tuxfamily.org edgy-pouit extra
```

> **BigWillyT said:**
> Does anyone know what's up with the repos?!?  Went home at lunch today after getting the NVIDIA drivers installed this morning and I can't find any of the beryl/emerald packages on any of the repos.  Someone please help!!!!  I gotta have my eyecandy! :)

Are you using the official beryl repos?

---

### Post by anodizer on 2006-10-20
```
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

## Beryl
deb http://www.beerorkid.com/compiz edgy main-edgy

## Penguin Liberation Front
##deb http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free
##deb-src http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free

## Seveas
deb http://seveas.imbrandon.com/ edgy-seveas all

## Misc
##deb http://www.elisanet.fi/mlind/ubuntu edgy fonts
##deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts
```

---

### Post by Uncle Spellbinder on 2006-10-20
My updated Edgy repos:

```
##################################
##### SUPPORTED/OFFICIAL UBUNTU-EDGY #####
##################################

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

##### MAJOR BUG FIX UPDATES
##(produced after the final release)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

##### UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

##### BACKPORTS REPOSITORY
##(Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
                                                                                                                                                                          
##### CANONICAL COMMERCIAL REPOSITORY
##(Hosted on Canonical servers, not Ubuntu servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

####################
##### UNSUPPORTED #####
####################

##### PLF
##(Please report any bug on [https://launchpad.net/products/plf/+bugs](https://launchpad.net/products/plf/+bugs))
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy-plf free non-free

##### LISTEN
deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen
##deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen listen-unstable
##deb-src [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen listen-unstable

##### AUTOMATIX 2
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

##### Treviño's Ubuntu Repository
##(for Flash 9 Beta)
##deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0
##deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0

##### Ubuntu Pouit Repository (v2) v6.10
##(for brasero)
deb [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit extra
deb-src [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit extra

##### BERYL
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy
deb-src [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy
##deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy
##deb-src [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy
##deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy
##deb-src [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy
##deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy
##deb-src [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy
```

---

### Post by benjaminzsj on 2006-10-21
If I have one repository and its mirror, will apt choose the faster one?

---

### Post by ashrack on 2006-10-23
I believe it will choose the closest one to your location

---

### Post by JMO707 on 2006-10-24
About the keys using the updated sources.list of Spellbinder:
[I]
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 18B52FE3521A9C7C
W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) edgy Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2D6CFB44DD800CD9
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy-plf Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY F120156012B83718
W: GPG error: [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY F120156012B83718[/I]

The Automatix one I know how to get it, but the rest I dont.

---

### Post by reacocard on 2006-10-24
For the keys, here's a nifty little trick.

Open a terminal, and type the following, replacing KEYSTRING with one of the long sets of letters and numbers returned by Synaptic/Apt:

```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys KEYSTRING
```

This should give you another code, something like 1F41B907. Enter this command, replacing KEYSTRING2 with the new one.

```
gpg --armor --export KEYSTRING2 > keyName.gpg
```

This will give you a file containing the gpg key. Use this command to add it.

```
sudo apt-key add keyName.gpg
```

Repeat the process for each repo, and the errors should go away.

---

### Post by JMO707 on 2006-10-24
Hey, that is nifty =J

Thanks. It solved the problem. I'll write it down =)

---

### Post by Mithrilhall on 2006-10-26
Okay...how come I don't see K9copy?

Does anyone have this showing up in their repositories?

---

### Post by deblover on 2006-10-26
here's mine:
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
##deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse
##deb-src http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

##### MAJOR BUG FIX UPDATES#####
##(produced after the final release)
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
##deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

##### UBUNTU SECURITY UPDATES #####
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
##deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

##### BACKPORTS REPOSITORY #####
##(Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
##deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
                                                                                                                                                                          
##### CANONICAL COMMERCIAL REPOSITORY #####
##(Hosted on Canonical servers, not Ubuntu servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

##### PLF REPOSITORY #####
##(Unsupported.  May contain illegal packages.  Use at own risk.)
#deb http://packages.freecontrib.org/plf edgy free non-free
#deb-src http://packages.freecontrib.org/plf edgy free non-free

##### PLF #####
##(Please report any bug on https://launchpad.net/products/plf/+bugs)
deb http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free

##### LISTEN #####
deb http://theli.free.fr/packages/ dapper listen
##deb http://theli.free.fr/packages/ dapper listen listen-unstable
##deb-src http://theli.free.fr/packages/ dapper listen listen-unstable

## Fonts
deb http://www.elisanet.fi/mlind/ubuntu edgy fonts

##### ntfs-3g #####
deb http://givre.cabspace.com/ubuntu/ edgy main-all

## Brasero (http://mrpouit.tuxfamily.org/dists/edgy-pouit/extra/)
deb http://mrpouit.tuxfamily.org edgy-pouit extra

## Seveas
deb http://seveas.imbrandon.com/ edgy-seveas all

##### Treviño's Ubuntu Repository
##(for Flash 9 Beta)
deb http://3v1n0.tuxfamily.org dapper 3v1n0
##deb-src http://3v1n0.tuxfamily.org dapper 3v1n0

```

---

### Post by Akoluth of Nandus on 2006-10-27
> **benjaminzsj said:**
> If I have one repository and its mirror, will apt choose the faster one?

If a Package is available in more than one repository from /etc/apt/sources.list then apt will use the repo with the newer version in it.
If the versions are equal then apt will choose the repo that is first mentioned.

---

### Post by cleverselfreferentialname on 2006-10-27
I'm very happy with mine this time around. A little new, so I don't know if anything conflicts yet.

```
#  Official
deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

# Proposed Multiverse
deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

# Bug fixes
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

# Security
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

# Backports
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

# Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu dapper-commercial main

# Beryl
deb http://dev.realistanew.com/beryl edgy beryl
deb-src http://dev.realistanew.com/beryl edgy beryl
deb http://beryl-mirror.lupine.me.uk/beryl edgy beryl
deb-src http://beryl-mirror.lupine.me.uk/beryl edgy beryl

# Penguin Liberation Front
#(Please report any bug on https://launchpad.net/products/plf/+bugs)
deb http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free

# Seveas
deb http://seveas.imbrandon.com/ edgy-seveas all

# Alberto Milone's drivers (thanks, dude)
deb http://albertomilone.com/drivers/unstable/edgy/32bit binary/

# Listen
#deb http://theli.free.fr/packages/ edgy listen

# Brasero
deb http://mrpouit.tuxfamily.org edgy-pouit extra
deb-src http://mrpouit.tuxfamily.org edgy-pouit extra

# Fonts
#deb http://www.elisanet.fi/mlind/ubuntu edgy fonts
#deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts

# NTFS-3g - NTFS driver with full read-write support. Experimental.
#deb http://givre.cabspace.com/ubuntu/ edgy main-all

# KDE - Latest KDE release
deb http://kubuntu.org/packages/kde-latest edgy main

# KOffice - Latest KOffice release
deb http://kubuntu.org/packages/koffice-latest/ edgy main

# Amarok - Latest Amarok release
deb http://kubuntu.org/packages/amarok-latest dapper main

# Konversation nighly builds
#deb http://imbrandon.com/packages edgy konversation-nightly
#deb-src http://imbrandon.com/packages edgy konversation-nightly

# Latest skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

# The Free TV Player. This is probably in french...haven't played with it yet.
deb http://www.tvfreeplayer.com/linux/ubuntu/dapper/ unstable main

# Debian Multimedia Repositories. Still applicable? Who knows.
# deb http://www.debian-multimedia.org stable main
# deb http://www.debian-multimedia.org experimental main
# deb-src http://www.debian-multimedia.org sid main
# deb http://people.ubuntubrasil.org/~rclbelem/lives/dapper/   binary/
# deb http://tutuxclan.free.fr/debs ./

# XDTV
deb http://nicolas.estre.free.fr/ubuntu dapper main
deb http://nicolas.estre.free.fr/ubuntu dapper experimental

# e17 (woot!)
deb http://SeerOfSouls.com/ edgy e17
deb-src http://SeerOfSouls.com/ edgy e17

```

---

### Post by Circus-Killer on 2006-10-30
does anyone by any chance happen to know of the repo which contains the most bleeding-edge wine version? :???: 

need to keep up the testing ;)

---

### Post by Akoluth of Nandus on 2006-10-30
> **Circus-Killer said:**
> does anyone by any chance happen to know of the repo which contains the most bleeding-edge wine version? :???:

Have a look at [the official wine page]("http://www.winehq.com/site/download-deb").
These are no cvs builds but nevertheless always the latest releases.

---

### Post by Circus-Killer on 2006-10-30
no Akoluth of Nandus, i found what i was looking for:

## Bleeding edge wine repository for Edgy
## only uncomment it if you need it
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

those repos are very up-to-date and reliable, just was struggling to find them. :???:

---

### Post by Akoluth of Nandus on 2006-10-30
> **Circus-Killer said:**
> no Akoluth of Nandus, i found what i was looking for:

## Bleeding edge wine repository for Edgy
## only uncomment it if you need it
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

those repos are very up-to-date and reliable, just was struggling to find them. :???:

Exactly these repos are mentioned on the wine site! 8)
You only have to replace "breezy" or "dapper" with "edgy" of course.

---

### Post by linuxguy on 2006-11-02
```
#################################
##### SUPPORTED/OFFICIAL UBUNTU-EDGY #####
#################################

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

##### MAJOR BUG FIX UPDATES
##(produced after the final release)
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

##### UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

##### BACKPORTS REPOSITORY
##(Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

##### CANONICAL COMMERCIAL REPOSITORY
##(Hosted on Canonical servers, not Ubuntu servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

####################
##### UNSUPPORTED #####
####################

##### PLF
##(Please report any bug on https://launchpad.net/products/plf/+bugs)
deb http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free

##### LISTEN
deb http://theli.free.fr/packages/ dapper listen
##deb http://theli.free.fr/packages/ dapper listen listen-unstable
##deb-src http://theli.free.fr/packages/ dapper listen listen-unstable

##### AUTOMATIX 2
deb http://www.getautomatix.com/apt edgy main

##### Treviño's Ubuntu Repository
##(for Flash 9 Beta)
##deb http://3v1n0.tuxfamily.org dapper 3v1n0
##deb-src http://3v1n0.tuxfamily.org dapper 3v1n0

##### Ubuntu Pouit Repository (v2) v6.10
##(for brasero)
deb http://mrpouit.tuxfamily.org edgy-pouit extra
deb-src http://mrpouit.tuxfamily.org edgy-pouit extra

##### BERYL
deb http://www.beerorkid.com/compiz edgy main-edgy
deb-src http://www.beerorkid.com/compiz edgy main-edgy
##deb http://media.blutkind.org/xgl/ edgy main-edgy
##deb-src http://media.blutkind.org/xgl/ edgy main-edgy
##deb http://compiz-mirror.lupine.me.uk/ edgy main-edgy
##deb-src http://compiz-mirror.lupine.me.uk/ edgy main-edgy
##deb http://ubuntu.compiz.net/ edgy main-edgy
##deb-src http://ubuntu.compiz.net/ edgy main-edgy
deb http://www.museek-plus.org/ubuntu edgy main

##### AMAROK
deb http://kubuntu.org/packages/amarok-144 edgy main
```

That's my list. I had some gpg key errors but thanks to reacocard's instructions I was able to generate them. For those of you who want to bypass the key-generating procedure, I uploaded them here:

[http://www.uploading.com/en/files/K8ECXZE2/key1.gpg.html](http://www.uploading.com/en/files/K8ECXZE2/key1.gpg.html)
[http://www.uploading.com/en/files/1Z0RC59A/key2.gpg.html](http://www.uploading.com/en/files/1Z0RC59A/key2.gpg.html)
[http://www.uploading.com/en/files/R0RZ7WP9/key3.gpg.html](http://www.uploading.com/en/files/R0RZ7WP9/key3.gpg.html)
[http://www.uploading.com/en/files/F21JEQNY/kubuntu_packages_jriddell_key.gpg.html](http://www.uploading.com/en/files/F21JEQNY/kubuntu_packages_jriddell_key.gpg.html)

# sudo apt-key add key1.gpg (and add the rest too). Hope that helps.

---

### Post by Yotsuba on 2006-11-03
```
## Official

# Ubuntu supported packages
deb http://tr.archive.ubuntu.com/ubuntu edgy main restricted
deb http://tr.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu supported packages / sources
deb-src http://tr.archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://tr.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu community supported packages
deb http://tr.archive.ubuntu.com/ubuntu edgy universe multiverse
deb http://tr.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse

# Ubuntu community supported packages / sources
deb-src http://tr.archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://tr.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

# Ubuntu backports packages
deb http://tr.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://tr.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

# Canonical commercial packages
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Non-Official

# Seveas packages
# Before update:
# wget http://seveas.theplayboymansion.net/seveas/1135D466.gpg -O- | sudo apt-key add -
deb http://seveas.theplayboymansion.net/seveas edgy-seveas all
deb-src http://seveas.theplayboymansion.net/seveas edgy-seveas all

# Plf packages
# Before update:
# wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add -
deb http://packages.freecontrib.org/ubuntu/plf edgy-plf free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf edgy-plf free non-free
```
Do I need the seveas packages?

---

### Post by visvak on 2006-11-05
since plf and cipherfunk are dead now. seveas is the only choice for multimedia packages like w32codecs and libdvdcss2 which are illegal in some countires and are therfore not included in the official repos.

answer : of course you need seveas's packages.

---

### Post by Yotsuba on 2006-11-05
thx vistak :) but plf seems to work :/

---

### Post by visvak on 2006-11-05
> **Yotsuba said:**
> thx vistak :) but plf seems to work :/

it was down for a while. its back up again now. From the PLF site (which BTW, is down now. i got this off google's cache)
```

**PLF Ubuntu new maintainers**

New maintainers for PLF Ubuntu were found, more info once everything is set up again.

**PLF ubuntu shutting down**

The PLF Ubuntu project is shutting down, due to lack of time of its maintainers. New volunteers are welcome.
PLF Ubuntu new maintainers
```

New maintainers for PLF Ubuntu were found, more info once everything is set up again.

---

### Post by FuzZy2006 on 2006-11-05
This is mine : ```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

##### MAJOR BUG FIX UPDATES#####
##(produced after the final release)
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

##### UBUNTU SECURITY UPDATES #####
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

##### BACKPORTS REPOSITORY #####
##(Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
                                                                                                                                                                          
##### CANONICAL COMMERCIAL REPOSITORY #####
##(Hosted on Canonical servers, not Ubuntu servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main


##### PLF #####
##(Please report any bug on https://launchpad.net/products/plf/+bugs)
deb http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free

##### LISTEN #####
deb http://theli.free.fr/packages/ dapper listen
##deb http://theli.free.fr/packages/ dapper listen listen-unstable
##deb-src http://theli.free.fr/packages/ dapper listen listen-unstable

##### Beryl #####
deb http://dev.realistanew.com/beryl edgy beryl
deb-src http://dev.realistanew.com/beryl edgy beryl
deb http://beryl-mirror.lupine.me.uk/beryl edgy beryl
deb-src http://beryl-mirror.lupine.me.uk/beryl edgy beryl

# Treviño's Beryl-SVN Ubuntu Repository
# GPG key: 81836EBF
deb http://3v1n0.tuxfamily.org edgy beryl-svn


# KDE - Latest KDE release
deb http://kubuntu.org/packages/kde-latest edgy main

# KOffice - Latest KOffice release
deb http://kubuntu.org/packages/koffice-latest/ edgy main

# Amarok - Latest Amarok release
deb http://kubuntu.org/packages/amarok-latest dapper main

# The Free TV Player. This is probably in french...haven't played with it yet.
deb http://www.tvfreeplayer.com/linux/ubuntu/dapper/ unstable main

# Debian Multimedia Repositories. Still applicable? Who knows.
deb http://www.debian-multimedia.org stable main
deb http://www.debian-multimedia.org experimental main
# deb-src http://www.debian-multimedia.org sid main
deb http://people.ubuntubrasil.org/~rclbelem/lives/dapper/ binary/
deb http://tutuxclan.free.fr/debs ./

# XDTV
deb http://nicolas.estre.free.fr/ubuntu dapper main
deb http://nicolas.estre.free.fr/ubuntu dapper experimental

# e17 (woot!)
deb http://SeerOfSouls.com/ edgy e17
deb-src http://SeerOfSouls.com/ edgy e17
##### UNOFFICAL REPOS #####

## Fonts
deb http://www.elisanet.fi/mlind/ubuntu edgy fonts
deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts

## Seveas
deb http://seveas.imbrandon.com/ edgy-seveas all

##### Treviño's Ubuntu Repository
##(for Flash 9 Beta)
deb http://3v1n0.tuxfamily.org dapper 3v1n0
deb-src http://3v1n0.tuxfamily.org dapper 3v1n0

##### Ubuntu Pouit Repository (v2) v6.10
##(for brasero)
deb http://mrpouit.tuxfamily.org edgy-pouit extra
deb-src http://mrpouit.tuxfamily.org edgy-pouit extra

####Wine####
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main

```
:KS

---

### Post by sunny_nwho on 2006-11-06
This is mine:
```

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb http://packages.freecontrib.org/ubuntu/plf/ edgy free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

## Uncomment the following two lines to fetch updated software from the network
#deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
#deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse
#deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu edgy-commercial main
#deb http://packages.freecontrib.org/plf/ edgy free non-free
#deb-src http://packages.freecontrib.org/plf/ edgy free non-free 
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf edgy-plf free non-free
deb-src http://packages.freecontrib.org/plf edgy-plf free non-free   
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

deb http://kubuntu.org/packages/koffice-16 edgy main

```

---

### Post by jkwarras on 2006-11-06
This mine.** For amd64 systems:**
```

## Main repository
deb http://es.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

## Updates
deb http://es.archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## Backports
deb http://es.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## Security updates
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## Proposed
deb http://es.archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu edgy-proposed main restriced universe multiverse

## Commercial repository
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Seveas repository
deb http://mirror.ubuntulinux.nl edgy-seveas all

## PLF 
deb http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free
# deb-src http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free

## Geole repository
deb http://ubuntu.geole.info/ edgy universe multiverse
# deb-src http://ubuntu.geole.info/ edgy universe multiverse
# deb http://ubuntu.geole.info/ edgy-backports main restricted universe multiverse
# deb-src http://ubuntu.geole.info/ edgy-backports main restricted universe multiverse

## Automatix
deb http://www.beerorkid.com/automatix/apt edgy main

## seb128 repository
deb http://people.ubuntu.com/~seb128/deb/ ./

## Janvitus Amd64 repository
deb http://janvitus.netsons.org/ubuntu/ edgy-janvitus all

## Debian Multimedia repository
deb http://www.debian-multimedia.org stable main
# deb http://www.debian-multimedia.org testing main
# deb http://www.debian-multimedia.org sid main
# deb http://www.debian-multimedia.org experimental main

## Debian Unofficial repository
deb http://ftp.debian-unofficial.org/debian stable main contrib non-free restricted

## Falcon generated repository
deb http://ubuntu.systemadministrator.org edgy all
# deb-src http://ubuntu.systemadministrator.org edgy all
# Mirrors
# deb http://ubuntu.moshen.de/ edgy
# deb-src http://ubuntu.moshen.de/ edgy

## Beryl XGL/Compiz repository
deb http://www.beerorkid.com/compiz edgy main-edgy main-edgy-amd64
# deb-src http://www.beerorkid.com/compiz edgy main-edgy main-edgy-amd64

## RareWares/Debian Multi-Media Repository for Unstable
deb http://www.rarewares.org/debian/packages/unstable/ ./

## Listen repository
deb http://theli.free.fr/packages/ dapper listen listen-unstable

## Musicbrainz update python-binding (for Listen)
deb http://users.musicbrainz.org/~luks/ubuntu dapper main

## Lprod repository
deb http://lprod.org/deb/dapper/ ./
# deb-src http://lprod.org/deb/dapper/ ./

## Cinelerra (se necesitan paquetes de Sid)
# deb http://labbs.net/~vale/debian ./

## ATI and NVIDIA Testing drivers
# deb http://albertomilone.com/drivers/edgy/nonlegacy/64bit binary/

## ATI and NVIDIA Unstable drivers
# deb http://albertomilone.com/drivers/unstable/edgy/64bit binary/

## Ralink RT2500 WiFi drivers
deb http://ubuntu.lupine.me.uk/ edgy lrm-amd64

## Ubuntu Pouit Repository
# deb http://mrpouit.tuxfamily.org edgy-pouit ati-drivers extra macbook openalchemist
# deb-src http://mrpouit.tuxfamily.org edgy-pouit ati-drivers extra macbook openalchemist

```

Note: Commented repositories works, but some of them have problems (i.e. cinelerra, since it needs Sid packages that doesn't fit too well with ubuntu packages) and others, I just don't need them right now.

---

### Post by Treviño on 2006-11-06
To long to post... :)

Here: [http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)

Please, digg it: [http://digg.com/linux_unix/Ubuntu_Edgy_Eft_COMPLETE_sources_list_repository_file_o](http://digg.com/linux_unix/Ubuntu_Edgy_Eft_COMPLETE_sources_list_repository_file_o)

---

### Post by gg234 on 2006-11-07
try here is the [big list of edgy source list ]("http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html")

---

### Post by Don_DiZzLe on 2006-11-09
I cant install mplayer rc1 using this repo deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0 because of this error:

mplayer:
  Depends: libfaac0 (>=1.24+cvs20060416) but 1.24clean-0ubuntu4 is to be installed

How do I fix this?

---

### Post by Treviño on 2006-11-09
It should be fixed now...
Simply sudo apt-get update and re-upgrade ;)

---

### Post by HAARP on 2006-11-09
**[color=#FF0000][size=14]I DONT RECOMMENED THIS LIST TO ANYONE![/size][/color]**
Seriously. It's huge. It's dangerous. And it will fsck up your system. Don't use my list.


```
# Official Ubuntu Edgy packages (GPG: 437D05B5)
deb http://de.archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb http://de.archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb http://de.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
#deb http://de.archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
#deb-src http://de.archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

# Ubuntu commercial packages
deb http://archive.canonical.com/ubuntu edgy-commercial main
deb-src http://archive.canonical.com/ubuntu edgy-commercial main

# Official Debian packages (GPG: 2D230C5F)
#deb http://ftp.debian.org/debian unstable main non-free contrib
#deb-src http://ftp.debian.org/debian unstable main non-free contrib

# Official MEPIS packages
deb http://apt.mepis.org/6.0/ mepis main

# kubuntu.org latest KDE (GPG: DD4D5088)
deb http://kubuntu.org/packages/kde-latest edgy main
deb http://kubuntu.org/packages/koffice-latest edgy main
deb http://kubuntu.org/packages/amarok-latest dapper main
deb-src http://kubuntu.org/packages/kde-latest edgy main
deb-src http://kubuntu.org/packages/koffice-latest edgy main
deb-src http://kubuntu.org/packages/amarok-latest dapper main

# Kubuntu Germany
deb http://archive.czessi.net/ubuntu edgy main restricted universe multiverse preview
deb-src http://archive.czessi.net/ubuntu edgy main restricted universe multiverse preview

# Ubuntu Lite
deb http://blueeyedcreature.net/ubuntu ./

# Debuntu packages
deb http://repository.debuntu.org/ edgy multiverse
deb-src http://repository.debuntu.org/ edgy multiverse

# Ubuntu NLP Repository (GPG key: 8ABD1965)
deb http://cl.naist.jp/~eric-n/ubuntu-nlp edgy nlp english delph-in misc
deb-src http://cl.naist.jp/~eric-n/ubuntu-nlp edgy nlp english delph-in misc

# Ubuntu Taiwan extra repository
deb http://apt.ubuntu.org.tw ubtw/
deb http://apt.ubuntu.org.tw ubtw-testing/
deb-src http://apt.ubuntu.org.tw ubtw/
deb-src http://apt.ubuntu.org.tw ubtw-testing/

# Ubuntu Dapper University Klagenfurt
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu uniklu-desktop uniklu-intern uniklu-nfsv4 uniklu-vserver ##uniklu-testing
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ dapper uniklu uniklu-desktop uniklu-intern uniklu-nfsv4 uniklu-vserver ##uniklu-testing

# Penguin Liberation Front
deb http://packages.freecontrib.org/plf edgy-plf free non-free
deb-src http://packages.freecontrib.org/plf edgy-plf free non-free

# Bazaar-NG development (GPG: 1F44842D)
deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./
deb-src http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# A little too quiet
deb http://apt.alittletooquiet.net/fab/ edgy main restricted universe multiverse
deb-src http://apt.alittletooquiet.net/fab/ edgy main restricted universe multiverse

# Achim's Kubuntu packages
deb http://www.mpe.mpg.de/~ach/kubuntu/dapper ./
deb http://www.mpe.mpg.de/~ach/kubuntu/dapper-experimental ./
deb-src http://www.mpe.mpg.de/~ach/kubuntu/dapper ./
deb-src http://www.mpe.mpg.de/~ach/kubuntu/dapper-experimental ./

# Asher256's packages
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french
deb-src http://asher256-repository.tuxfamily.org dapper main dupdate french
deb-src http://asher256-repository.tuxfamily.org ubuntu main dupdate french

# Cafuego's packages (GPG: 969F3F57)
deb http://ubuntu.cafuego.net/ edgy-cafuego all bcm43xx
deb-src http://ubuntu.cafuego.net/ edgy-cafuego all bcm43xx

# Candyz's repository
deb http://cle.linux.org.tw/candyz/Ubuntu/edgy i386/

# Cerkinfo's repository
deb http://apt.cerkinfo.be/ unstable main contrib
deb-src http://apt.cerkinfo.be/ unstable main contrib

# Directhex's stuff
deb http://directhex.mfgames.com/ ./
deb-src http://directhex.mfgames.com/ ./

# Doc.Horn's packages (GPG: 2F306651)
deb http://ubuntu.systemadministrator.org edgy all
deb-src http://ubuntu.systemadministrator.org edgy all

# Gauvain's repository
deb http://gauvain.tuxfamily.org/repos edgy contrib
deb-src http://gauvain.tuxfamily.org/repos edgy contrib

# Geole's repository
deb http://ubuntu.geole.info/ edgy universe multiverse
deb-src http://ubuntu.geole.info/ edgy universe multiverse

# Imbrandons software repository (GPG key: 887D9FD2)
deb http://www.imbrandon.com/packages edgy all
deb-src http://www.imbrandon.com/packages edgy all

# Ion's Ubuntu packages (GPG key: 2EE24E0B)
deb http://johan.kiviniemi.name/ubuntu edgy falcon gift-turtle gwget rubygems ##lrm
deb-src http://johan.kiviniemi.name/ubuntu edgy falcon gift-turtle gwget rubygems ##lrm

# Janvitus AMD64 repository
deb http://janvitus.netsons.org/ubuntu/ edgy-janvitus all
deb-src http://janvitus.netsons.org/ubuntu edgy-janvitus all

# lprod packages
deb http://lprod.org/deb/dapper/ ./
deb-src http://lprod.org/deb/dapper/ ./

# MaXeR's repository (GPG: 35A92053)
deb http://repos.knio.it/ breezy main contrib non-free
deb-src http://repos.knio.it/ breezy main contrib non-free

# mlind's packages (GPG: D0AFFF5E937215FF)
deb http://www.elisanet.fi/mlind/ubuntu edgy main fonts
deb-src http://www.elisanet.fi/mlind/ubuntu edgy main fonts

# Morgoth backports
deb http://morgoth.free.fr/ubuntu edgy-backports main
deb-src http://morgoth.free.fr/ubuntu edgy-backports main

# Pouit Repository
deb http://mrpouit.tuxfamily.org edgy-pouit extra
deb-src http://mrpouit.tuxfamily.org edgy-pouit extra

# Raphink's unofficial packages
deb http://packages.raphink.net/ubuntu dapper main
deb-src http://packages.raphink.net/ubuntu dapper main

# Rarewares Multimedia Repository
deb http://www.rarewares.org/debian/packages/unstable/ ./

# seb128's repository
deb http://people.ubuntu.com/~seb128/deb ./
deb-src http://people.ubuntu.com/~seb128/deb ./

# SeerOfSouls
deb http://SeerOfSouls.com/ edgy e17 contrib
deb-src http://SeerOfSouls.com/ edgy e17 contrib

# Seveas' packages (GPG: 1135D466)
deb http://seveas.theplayboymansion.net/seveas edgy-seveas all
deb-src http://seveas.theplayboymansion.net/seveas edgy-seveas all

# Thomas' packages
deb http://thomas.enix.org/pub/debian/packages/ edgy main
deb-src http://thomas.enix.org/pub/debian/packages/ edgy main

# Treviño's repository (GPG: 81836EBF/DD800CD9)
deb http://3v1n0.tuxfamily.org edgy 3v1n0 beryl-svn ##suspend2
deb-src http://3v1n0.tuxfamily.org edgy 3v1n0 beryl-svn ##suspend2

# AfterBirth repository
deb http://www.voxpopulimedia.com/debian dapper main

# Audacious
deb http://vdlinux.sourceforge.jp/ experimental audacious
deb-src http://vdlinux.sourceforge.jp/ experimental audacious

# Automatix
deb http://www.getautomatix.com/apt edgy main

# Bleeding Edge Drivers
#deb http://www.albertomilone.com/drivers/edgy/legacy/32bit binary/
#deb http://www.albertomilone.com/drivers/edgy/nonlegacy/32bit binary/
#deb http://albertomilone.com/drivers/unstable/edgy/32bit binary/

# BMPx
deb http://randrianiriana.org/debian/ ./
deb http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/ ./
deb http://files.beep-media-player.org/packages/ubuntu edgy main universe testing
deb-src http://files.beep-media-player.org/packages/ubuntu edgy main universe testing

# Cinelerra & Mjpegtools
#deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./
#deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/ ./
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
#deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./
#deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/ ./
deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./
deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./

# debian.wgdd.de Ubuntu Repository (GPG key: E394D996)
deb http://debian.wgdd.de/ubuntu dapper universe
deb-src http://debian.wgdd.de/ubuntu dapper universe

# Debian Multimedia
deb http://www.debian-multimedia.org sid main
deb-src http://www.debian-multimedia.org sid main

# Quinn's Compiz
deb http://www.beerorkid.com/compiz edgy main-edgy
deb-src http://www.beerorkid.com/compiz edgy main-edgy

# Freedesktop's Compiz
deb http://gandalfn.club.fr/ubuntu/ edgy .
deb http://gandalfn.club.fr/ubuntu/ edgy-misc .
deb http://gandalfn.club.fr/ubuntu/ edgy-dev .

# Compiztools
deb http://compiztools.free.fr/debian unstable main

# Easycam
deb http://blognux.free.fr/debian unstable main

# Easyubuntu
deb http://easyubuntu.cafuego.net main easyubuntu
deb-src http://easyubuntu.cafuego.net main easyubuntu

# Ekiga & Debian pkg-voip
deb http://snapshots.seconix.com/ubuntu/ edgy main
deb http://pkg-voip.buildserver.net/ubuntu edgy main
deb-src http://snapshots.seconix.com/ubuntu/ edgy main
deb-src http://pkg-voip.buildserver.net/ubuntu edgy main

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

# MythTV
deb http://home.eng.iastate.edu/~superm1 edgy all
deb-src http://home.eng.iastate.edu/~superm1 edgy all

# NTFS-3G & Fuse
deb http://flomertens.keo.in/ubuntu/ edgy main
deb-src http://flomertens.keo.in/ubuntu/ edgy main

# Opera
deb http://deb.opera.com/opera unstable non-free

# Picard (GPG: 92132F7B)
deb http://users.musicbrainz.org/~luks/ubuntu dapper main
deb-src http://users.musicbrainz.org/~luks/ubuntu dapper main

# Ralink RT2500 WiFi drivers
deb http://ubuntu.lupine.me.uk/ edgy all

# Samba
deb http://www.linux2go.dk/ubuntu edgy main
deb-src http://www.linux2go.dk/ubuntu edgy main

# Sinhala
deb http://sinhala.sourceforge.net/debian/i386/dapper/ ./

# Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Suspend2 repository
deb http://dagobah.ucc.asn.au/ubuntu-suspend2 dapper/
deb-src http://dagobah.ucc.asn.au/ubuntu-suspend2 dapper/

# Tvfreeplayer Packages
deb http://www.tvfreeplayer.com/linux/ubuntu/dapper/ unstable main

# VLC nightlies (GPG: 81CACA84)
deb http://nightlies.videolan.org/build/dapper-i386 /
deb-src http://nightlies.videolan.org/build/dapper-i386 /

# Wine
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main

# XDTV
deb http://nicolas.estre.free.fr/ubuntu dapper main experimental

# DarkMageZ Repo
deb http://mirror.randumb.org/darkmagez/repo dapper-darkmagez all
deb-src http://mirror.randumb.org/darkmagez/repo dapper-darkmagez all
deb http://mirror.randumb.org/darkmagez/repo edgy-darkmagez all
deb-src http://mirror.randumb.org/darkmagez/repo edgy-darkmagez all

# Doomsday (GPG: 4B6E7209)
deb http://eyagi.bpa.nu/~jamie/ubuntu edgy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu edgy main restricted universe multiverse

# Spring
deb ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /
deb-src ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /

# -------------------------------------------------------------------------------------------------
# gpg --keyserver subkeys.pgp.net --recv <KEY>; gpg --export --armor <KEY> | sudo apt-key add -

```

---

### Post by mrfoobar on 2006-11-09
I don't know if anyone else has had this problem, but on my machine Treviño's version of mozilla-mplayer causes firefox 2.0 to stop recognizing the plugin.   Also, his repository seems to force synaptic to change the wpasupplicant package which ended up killing my network connectivity upon reboot(I'm using ipw3945 drivers and network-manager).  If you have a similar configuration to mine (ipw3945/network-manager), you might want to be careful about using his repository.

---

### Post by Don_DiZzLe on 2006-11-10
Does anyone else have any problems with mlind's repo's (deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy fonts main, deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy experimental) , adding the gpgkey is not working. I get this:

gpg &#8211;keyserver subkeys.pgp.net &#8211;recv 937215FF

gives me an $ gpg &#8211;keyserver subkeys.pgp.net &#8211;recv 937215FF
gpg: directory `/home/rhandulle/.gnupg' created
gpg: new configuration file `/home/rhandulle/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/rhandulle/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/rhandulle/.gnupg/secring.gpg' created
gpg: keyring `/home/rhandulle/.gnupg/pubring.gpg' created
usage: gpg [options] [filename]

and then this

gpg &#8211;export &#8211;armor 937215FF | sudo apt-key add -

gives me an

gpg &#8211;export &#8211;armor 937215FF | sudo apt-key add -
Password:usage: gpg [options] [filename]

---

### Post by Yotsuba on 2006-11-10
i see that still many people use dapper repos for edgy, wouldn't that may cause problem?

---

### Post by ubu_dynamite on 2006-11-10
## If you get errors about missing keys, lookup the key in this file
## and run these commands (replace KEY with the key number)
##################################################
## gpg --keyserver subkeys.pgp.net --recv KEY
## gpg --export --armor KEY | sudo apt-key add -
##################################################
## OFFICIALLY SUPPORTED REPOSITORIES 'main restricted'
## COMMUNITY SUPPORTED REPOSITORIES 'universe multiverse'
##
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
##################################################

## BACKPORTS "official backports"
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse


## dapper-commercial by canonical
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main


## Bleeding edge (official) wine repository for Edgy
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
# deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main


## MP3 w32codecs
## wget [http://mirror.ubuntulinux.nl/1135D466.gpg](http://mirror.ubuntulinux.nl/1135D466.gpg) -O- | sudo apt-key add -
# deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) edgy-seveas extras seveas-meta

---

### Post by BLTicklemonster on 2006-11-11
DO NOT USE THE FOLLOWING, UPDATE, UPGRADE, THEN BOOT TO RECOVERY, THEN TYPE STARTX UNLESS YOU WANT TO SEE THIS:

[http://ubuntuforums.org/showthread.php?t=297814](http://ubuntuforums.org/showthread.php?t=297814)


```
# Treviño's Ubuntu Edgy Sources list
# http://3v1n0.tuxfamily.org/blog/?page_id=13
#
# Firstly made on source-o-matic (http://www.ubuntulinux.nl/source-o-matic) list
# Added many extra repository
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
#  gpg --keyserver subkeys.pgp.net --recv KEY
#  gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
#  wget URL --quiet -O - | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
#  sudo apt-key add FILE
#


# Ubuntu supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ edgy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe #Added by software-properties

# Ubuntu community supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-security universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed universe multiverse

# Ubuntu backports project (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse #Added by software-properties

# CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
# RealPlayer10, Opera and more to come.)
deb http://archive.canonical.com/ubuntu edgy-commercial main

# Seveas' packages (GPG key: 1135D466)
deb http://mirror.ubuntulinux.nl edgy-seveas all
deb-src http://mirror.ubuntulinux.nl edgy-seveas all

# kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest edgy main
deb-src http://kubuntu.org/packages/kde-latest edgy main
deb http://kubuntu.org/packages/kde4-3.80.2 ./

# kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)
deb http://kubuntu.org/packages/koffice-latest edgy main
deb-src http://kubuntu.org/packages/koffice-latest edgy main

# kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest edgy main
deb-src http://kubuntu.org/packages/amarok-latest edgy main
deb http://kubuntu.org/packages/amarok-144 edgy main

# Bleeding edge wine packages
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main

# The Opera browser (packages) (GPG key: 6A423791)
deb http://deb.opera.com/opera etch non-free

# Google picasa packages
deb http://dl.google.com/linux/deb/ stable non-free

# Penguin Liberation Front
deb http://packages.freecontrib.org/ubuntu/plf edgy-plf non-free free
deb-src http://packages.freecontrib.org/ubuntu/plf edgy-plf non-free free
deb http://mrpouit.free.fr/plf-fallback edgy-plf free non-free
deb-src http://mrpouit.free.fr/plf-fallback edgy-plf free non-free

# Pouit repository- Ubuntu 6.10 "edgy eft" (GPG key: 12B83718)
deb http://download.tuxfamily.org/pouit edgy extra openalchemist ati-drivers #macbook
deb-src http://download.tuxfamily.org/pouit edgy extra openalchemist ati-drivers #macbook

## archive.kubuntu.de / archive.czessi.net
# The repository from Kubuntu Germany
# wget http://archive.czessi.net/ubuntu/kczessi.gpg
# sudo apt-key add kczessi.gpg
deb http://archive.czessi.net/ubuntu edgy main restricted universe multiverse preview
deb-src http://archive.czessi.net/ubuntu edgy main restricted universe multiverse preview

# E-Yagi Consulting Community Repository (GPG: 4B6E7209)
deb http://eyagi.bpa.nu/~jamie/ubuntu edgy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu edgy main restricted universe multiverse

# Ubuntu Taiwan ubuntu extra repository
deb http://apt.ubuntu.org.tw ubtw/
deb http://apt.ubuntu.org.tw ubtw-testing/

# # Achim's Unofficial 'edgy' Kubuntu packages
deb http://www.mpe.mpg.de/~ach/kubuntu/edgy ./
deb-src http://www.mpe.mpg.de/~ach/kubuntu/edgy ./

# # Ubuntu edgy University Klagenfurt packages
# # $ wget http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub
# # $ sudo apt-key add uniklu-debuild.pub 
# #   uniklu:         backports and new packages   
# #   uniklu-desktop: packages for uniklu desktop
# #   uniklu-intern:  not freely redistributable (jvm), or modified packages
# #   uniklu-nfsv4:   nfsv4 kernel and packages
# #   uniklu-vserver: vserver kernel
# #   uniklu-testing: packages not ready for general use !
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-desktop
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-intern
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-nfsv4
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-vserver
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-testing
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-desktop
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-intern
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-nfsv4
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-vserver
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-testing

## SimplyMepis packages (distro based on k-ubuntu)
deb http://apt.mepis.org/6.0/ mepis main

# Ekiga and Debian pkg-voip
deb http://pkg-voip.buildserver.net/ubuntu edgy main

# superm1's repository (mythtv and other nonfree) (GPG: 80DF6D58)
deb http://home.eng.iastate.edu/~superm1 edgy all
deb-src http://home.eng.iastate.edu/~superm1 edgy all

# Official Beryl Ubuntu Packages
# GPG key-file: http://ubuntu.beryl-project.org/quinn.key.asc
deb http://ubuntu.beryl-project.org/ edgy main-edgy
deb http://www.beerorkid.com/compiz edgy main-edgy

# Freedesktop compiz packages
deb http://gandalfn.club.fr/ubuntu/ edgy .
deb http://gandalfn.club.fr/ubuntu/ edgy-misc .
deb http://gandalfn.club.fr/ubuntu/ edgy-dev .

# Subpixel Font rendering packages
# Improved font rendering - May violate some patents
deb http://www.elisanet.fi/mlind/ubuntu edgy fonts main
deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts main

# Others mlind experimental misc Packages
deb http://www.elisanet.fi/mlind/ubuntu edgy experimental
deb-src http://www.elisanet.fi/mlind/ubuntu edgy experimental

# Skype packages
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Easycam packages
deb http://blognux.free.fr/debian unstable main

# Audacious
deb http://vdlinux.sourceforge.jp/ experimental audacious
deb-src http://vdlinux.sourceforge.jp/ experimental audacious

## Listen
deb http://theli.free.fr/packages/ dapper listen theli listen-unstable
deb-src http://theli.free.fr/packages/ dapper listen theli listen-unstable

# Geole's Ubuntu Repository
# wget http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg
# sudo apt-key add geole-apt-key.gpg
deb http://ubuntu.geole.info/ edgy universe multiverse

# Linux2Go Ubuntu Packages (GPG key: E8BDA4E3)
deb http://www.linux2go.dk/ubuntu edgy main
deb-src http://www.linux2go.dk/ubuntu edgy main

# GCompris, Televidilo, Kdocker, Frozen-Bubble...
deb http://thomas.enix.org/pub/debian/packages/ edgy main
deb-src http://thomas.enix.org/pub/debian/packages/ edgy main

# Asher256's Repository
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

# Gauvain Repository
deb http://gauvain.tuxfamily.org/repos edgy contrib
deb-src http://gauvain.tuxfamily.org/repos edgy contrib

# Tvfreeplayer Packages
deb http://www.tvfreeplayer.com/linux/ubuntu/dapper/ unstable main

# gnomemeeting - ekiga (GPG key: 52ABFCB1)
deb http://snapshots.ekiga.net/ubuntu/ edgy main
deb-src http://snapshots.ekiga.net/ubuntu/ edgy main
deb http://snapshots.voxgratia.org/ubuntu/ edgy main
deb-src http://snapshots.voxgratia.org/ubuntu/ edgy main

# seb128 repository (gaim - rhythmbox)
deb http://people.ubuntu.com/~seb128/deb ./
deb-src http://people.ubuntu.com/~seb128/deb ./

## lprod packages: many audio/video apps: avidemux, cinelerra...
deb http://lprod.org/deb/edgy/ ./
deb-src http://lprod.org/deb/edgy/ ./

## Mjpegtools and Cinelerra packages (choose your arch)
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./
##deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/ ./
##deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./
deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./
##deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/ ./
##deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./
 
## LiVes dapper package 
deb http://people.ubuntubrasil.org/~rclbelem/lives/edgy/ ./binary/

## A little too quiet
deb http://apt.alittletooquiet.net/staging dapper main

## Jahshaka Packages
deb http://repo.jahshaka.org/ubuntu/dapper binary-i386/

## Spring Packages
deb ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /
deb-src ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /

## debian.wgdd.de Ubuntu Repository (GPG key: E394D996)
deb http://debian.wgdd.de/ubuntu edgy universe
deb-src http://debian.wgdd.de/ubuntu edgy universe

## VLC nightlies
deb http://nightlies.videolan.org/build/edgy-i386 /

# Cafuego's edgy Stuff: Broadcom firmware, google-earth, beagle (GPG key: 969F3F57)...
deb http://au.ubuntu.cafuego.net edgy-cafuego all bcm43xx
deb-src http://au.ubuntu.cafuego.net edgy-cafuego all bcm43xx

# Debuntu Ubuntu edgy packages
# GPG Key: http://repository.debuntu.org/GPG-Key-chantra.txt
deb http://repository.debuntu.org/ edgy multiverse
deb-src http://repository.debuntu.org/ edgy multiverse

# BMPx edgy Repository
# GPG key-file: http://files.beep-media-player.org/packages/bmp-packages.pubkey
deb http://files.beep-media-player.org/packages/ubuntu edgy main universe testing
deb-src http://files.beep-media-player.org/packages/ubuntu edgy main universe testing

# Morgoth Repository (Monkey's Audio, xmms pugins, vlc plugins, gqview, audacity...)
deb http://morgoth.free.fr/ubuntu edgy-backports main
deb-src http://morgoth.free.fr/ubuntu edgy-backports main

# ATi & nVidia drivers Ubuntu packages
# GPG key: http://albertomilone.com/drivers/tseliot.asc
deb http://albertomilone.com/drivers/unstable/edgy/32bit binary/
deb http://albertomilone.com/drivers/edgy/nonlegacy/32bit binary/

## Latest Nvidia drivers in restricted modules packages
deb http://amaranth.selfip.com/ edgy lrm
deb-src http://amaranth.selfip.com/ edgy lrm

# Givre's repository (ntfs-3g & fuse 2.5.3) - NTFS writing support
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main
deb-src http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main

# Automatix (GPG key: 521A9C7C)
deb http://www.getautomatix.com/apt edgy main

# SoS: SeerOfSouls - e17
# GPG-Key: http://seerofsouls.com/keys/hawkwind.asc
deb http://SeerOfSouls.com/ edgy e17 contrib
deb-src http://SeerOfSouls.com/ edgy contrib e17

# XDTV
deb http://nicolas.estre.free.fr/ubuntu dapper main experimental

# Musicbrainz
deb http://users.musicbrainz.org/~luks/ubuntu edgy musicbrainz
deb-src http://users.musicbrainz.org/~luks/ubuntu edgy musicbrainz

# imbrandons software repository (GPG key: 887D9FD2)
deb http://www.imbrandon.com/packages edgy all
deb-src http://www.imbrandon.com/packages edgy all

# Candyz's Ubuntu Packages
# GPG key: http://cle.linux.org.tw/candyz/Ubuntu/candyz.key
deb http://cle.linux.org.tw/candyz/Ubuntu/edgy i386/

# The Ubuntu NLP Repository (GPG key: 8ABD1965)
deb http://cl.naist.jp/~eric-n/ubuntu-nlp edgy nlp english delph-in misc
deb-src http://cl.naist.jp/~eric-n/ubuntu-nlp edgy nlp english delph-in misc

# Ubuntu System Administrator packages
# mirror: http://ubuntu.moshen.de
deb http://ubuntu.systemadministrator.org edgy all
deb-src http://ubuntu.systemadministrator.org edgy all

# Ion's Ubuntu packages (GPG key: 2EE24E0B)
deb http://johan.kiviniemi.name/ubuntu edgy all
deb-src http://johan.kiviniemi.name/ubuntu edgy all

# Treviño's Ubuntu edgy Repository (GPG key: 81836EBF - DD800CD9)
# Many "random" software: aMule, amsn, mplayer, moto4lin, flashplugin & flashplayer (9.x)...
# Further informations: http://3v1n0.tuxfamily.org
deb http://3v1n0.tuxfamily.org edgy 3v1n0
deb-src http://3v1n0.tuxfamily.org edgy 3v1n0

# Treviño's Ubuntu edgy Beryl-SVN Repository (GPG key: 81836EBF - DD800CD9)
# Daily Updated Beryl (and related projects) Packages...
deb http://3v1n0.tuxfamily.org edgy beryl-svn

## Treviño's Ubuntu Suspend2 patched kernels Repository (GPG key: 81836EBF - DD800CD9)
## Ubuntu kernels patched with Suspend2 plus other related tools www.suspend2.net
## Warning: they will replace standard ubuntu kernel related packages
deb http://3v1n0.tuxfamily.org edgy suspend2
deb-src http://3v1n0.tuxfamily.org edgy suspend2

```

I about wet my pants when I saw that. Something up there messed up my /etc/sudoers.

---

### Post by Bullwinkle_Moose on 2006-11-12
There is a discussion of this problem right on [Treviño's page]("http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/"), if you scroll down in the comments, starting with comment number 139.

Basically, the problem files are kubuntu-default-settings and possibly kubuntu-artwork-usplash.  If you revert these back to version 1:6.10-61 the ominous messages should disappear.

However, it troubles me (as it apparently does some commenters) that someone would do something like this in an attempt to keep Ubuntu users in a "walled garden."  This "helpful warning" could be seen by some as an attempt to start a Ubuntu "cult", where you're not allowed to seek out any information or software from outside the  "cult" without fear of repercussion from within.

Whoever came up with these bogus packages needs several good swift kicks in the posterior, IMHO!

---

### Post by Treviño on 2006-11-12
Iom's repository is the cause to that... :(

For ubuntu users the packages should be [usplash-theme-ubuntu]("http://packages.ubuntu.com/edgy/misc/usplash-theme-ubuntu") and [edgy-wallpapers]("http://packages.ubuntu.com/edgy/x11/edgy-wallpapers").

---

### Post by BLTicklemonster on 2006-11-12
Well, the way that it redid my wallpaper and would not let me change it, was that because it was meant for a different distro, and was installed in such a way that ubuntu's change wallpaper thing was unable to work?

And that whole changing sudoers... whatever did that totally creeped me out. Years ago, I had gotten windows viruses and all, but never had anything happen like that!

---

### Post by raycast on 2006-11-15
Moral of the story:

**[SIZE="7"]DON'T ADD EVERY REPOSITORY YOU CAN FIND.[/SIZE]**

**ONLY** use repositories that you can **TRUST**.

And especially never trust some repository just because someone else referred to it by listing his apt/sources.list contents.

---

### Post by BLTicklemonster on 2006-11-15
Well, if you put it that way, okay then. :mrgreen:

---

### Post by savohead on 2006-11-15
eheh, right said and i'm with you (even if i'm an "untrusted" user), but don't you think that [my idea]("http://ubuntuforums.org/showthread.php?t=299376") could be of some use with that?! Telling new users to use just the lists in that place?!
bye

---

### Post by The Warlock on 2006-11-15
> **Bullwinkle_Moose said:**
> There is a discussion of this problem right on [Treviño's page]("http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/"), if you scroll down in the comments, starting with comment number 139.

Basically, the problem files are kubuntu-default-settings and possibly kubuntu-artwork-usplash.  If you revert these back to version 1:6.10-61 the ominous messages should disappear.

However, it troubles me (as it apparently does some commenters) that someone would do something like this in an attempt to keep Ubuntu users in a "walled garden."  This "helpful warning" could be seen by some as an attempt to start a Ubuntu "cult", where you're not allowed to seek out any information or software from outside the  "cult" without fear of repercussion from within.

Whoever came up with these bogus packages needs several good swift kicks in the posterior, IMHO!

You should be thanking him.

The repository in question stored a bunch of expiremental beta nVidia drivers that were crashing a bunch of programs. Trevino just threw the repo in there with all the others and a bunch of idiots copied his list and installed it and a whole bunch of other potentially system-raping packages.

You should not EVER list repositories or install packages if you don't even know what they are. That goes for any operating system.

It's not a "culty walled-garden" or whatever crap; it's unknown software on your computer. Don't install packages or add repositories if you don't have a clue what's in them or why you'd want them. Is it too much to ask that a computer user do a little basic research on the software they're installing on their computer?

---

### Post by Don_DiZzLe on 2006-11-20
Trevino: why do u have 2 mplayer firefox-plugins; mozilla-mplayer & mplayerplug-in ?

They both dont seem to work anyways.

---

### Post by zgerrz on 2006-11-21
> **Don_DiZzLe said:**
> Trevino: why do u have 2 mplayer firefox-plugins; mozilla-mplayer & mplayerplug-in ?

They both dont seem to work anyways.

Also, the latest update to the non free flash plugin is broke. Don't know why you bothered to update it if it's gonna be broken now.

---

### Post by Don_DiZzLe on 2006-11-22
I didnt know the mplayer pluging were broken, but flash beta2 works just fine now that it has been fixed in AX2

---

