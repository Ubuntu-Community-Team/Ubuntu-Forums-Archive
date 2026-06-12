---
title: "Repository errors"
date: 2006-12-10
forum: Repositories &amp; Backports
---

### Post by Johan! on 2006-12-10
When I try to reload the package information in Synaptic, I see a lot of errors.
As you can see in the screenshot, there are quite a number of translation files that synaptic could not download.

Is this normal?

---

### Post by ciscosurfer on 2006-12-10
> **Johan! said:**
> When I try to reload the package information in Synaptic, I see a lot of errors.
As you can see in the screenshot, there are quite a number of translation files that synaptic could not download.

Is this normal?You need to make sure that you have gpg signed signatures for those repos that need them.

This article on the wiki will help you get started: [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

---

### Post by Johan! on 2006-12-10
I have the keys for the normal ubuntu repo's:
```

sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

...and more keys...

```

---

### Post by ciscosurfer on 2006-12-10
> **Johan! said:**
> I have the keys for the normal ubuntu repo's:
```

sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

...and more keys...

```Two points: the repos you are trying to download from may be down, and/or they will need their respective gpg keys.  From what I can see, you probably need your freecontrib key, budgetdedicated key, and your beryl key.

Please post the output of **cat /etc/apt/sources.list**

---

### Post by Johan! on 2006-12-10
This is part of the apt-get update output:
```
sudo apt-get update
Get:1 http://repository.debuntu.org edgy Release.gpg [189B]
Get:2 http://nl.archive.ubuntu.com edgy Release.gpg [191B]                                                                                                  
**Ign http://nl.archive.ubuntu.com edgy/main Translation-en_US                                                            **                                    
Get:3 http://mirror.ubuntulinux.nl edgy-seveas Release.gpg [307B]                                                                                           
**Ign http://repository.debuntu.org edgy/multiverse Translation-en_US                                                                   **                      
Get:4 http://archive.canonical.com edgy-commercial Release.gpg [191B]                                                                                       
[B]Ign http://archive.canonical.com edgy-commercial/main Translation-en_US                                                                                     
Ign http://wine.budgetdedicated.com edgy Release.gpg      [/B]                                                                                                  
**Ign http://wine.budgetdedicated.com edgy/main Translation-en_US**                                                                                             
Get:5 http://security.ubuntu.com edgy-security Release.gpg [191B]                                                                                           
**Ign http://security.ubuntu.com edgy-security/main Translation-en_US** 
```

synaptic tells me that some files failed, and apt-get is ignoring them.

nl.archive.ubuntu.com is an official mirror, and I have the key, still it fails to download the translation file.
security.ubuntu.com is also a normal repository.

---

### Post by Johan! on 2006-12-10
sources.list:

```

# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://nl.archive.ubuntu.com/ubuntu edgy main restricted
deb http://nl.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://nl.archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://nl.archive.ubuntu.com/ubuntu edgy universe multiverse
deb http://nl.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://nl.archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## Nvidia drivers Tseliot
deb http://www.albertomilone.com/drivers/edgy/nonlegacy/32bit binary/

## Pouit repository- Ubuntu 6.10 "edgy eft" brasero etc.
deb http://download.tuxfamily.org/pouit edgy extra openalchemist
# deb-src http://download.tuxfamily.org/pouit edgy extra openalchemist

## PLF
## Please report any bug on https://launchpad.net/products/plf/+bugs
deb http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free

## beryl etc.
deb http://ubuntu.beryl-project.org/ edgy main
deb http://beryl-mirror.lupine.me.uk edgy main
deb-src http://beryl-mirror.lupine.me.uk edgy main

## Seveas repos https://wiki.ubuntu.com/SeveasPackages
deb http://mirror2.ubuntulinux.nl edgy-seveas all
#deb http://mirror.ubuntulinux.nl/ edgy-seveas all
#deb-src http://mirror.ubuntulinux.nl/ edgy-seveas all

## Wine
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main

## edgy-commercial by canonical
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Cafuego’s Edgy Stuff: Broadcom kernel firmwares, google-earth, beagle
deb http://au.ubuntu.cafuego.net edgy-cafuego all
deb-src http://au.ubuntu.cafuego.net edgy-cafuego all

## Debuntu.org 
deb http://repository.debuntu.org/ edgy multiverse
deb-src http://repository.debuntu.org/ edgy multiverse

## Treviño’s Ubuntu Dapper Repository
## Many “random” software: aMule, amsn, gnash, google-earth, stellarium, moto4lin
deb http://download.tuxfamily.org/3v1deb edgy 3v1n0
deb-src http://download.tuxfamily.org/3v1deb edgy 3v1n0

## Ubuntu Edgy Proposed
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe

## Murrina themes etc. http://malteo.homelinux.net/
#deb http://malteo.homelinux.net edgy-malteo all
#deb-src http://malteo.homelinux.net edgy-malteo all 

```

---

### Post by ciscosurfer on 2006-12-10
That quite an extensive list!

What you can do, in the meantime, is actually go to the Web sites that your sources.list file reference.  For instance, if you want to see if there is a new updated .deb file from [http://nl.archive.ubuntu.com/](http://nl.archive.ubuntu.com/), you can check out the site and download the .deb you like.

All of those sites, btw, can be hit through a browser, and aren't currently down.

I would recommend that you make sure that you have all the correct gpg keys associated first (System > Administration > Software Sources), then issue ```
sudo aptitude update && sudo aptitude upgrade && sudo aptitude dist-upgrade
```from within a terminal.

---

### Post by Johan! on 2006-12-10
I can update normally, so that's no problem.:) 

I was wondering why I see the ignored/failed downloads.

```
sudo aptitude update && sudo aptitude upgrade && sudo aptitude dist-upgrade
```
didn't upgrade anything

---

### Post by ciscosurfer on 2006-12-10
> **Johan! said:**
> [...]I was wondering why I see the ignored/failed downloads.Yes, and that's why I've mentioned that you need to make sure your gpg signatures match up with the lines in your sources.list :D

---

### Post by Johan! on 2006-12-10
By the way, is it possible that Ubuntu ignores the translation files, because the language I installed is en-US?

I also installed the Dutch language packs.

And if a repository is not gpg signed, does Ubuntu ignore the gpg file?

signatures:
```
sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>
...

```

---

### Post by ciscosurfer on 2006-12-10
> **Johan! said:**
> By the way, is it possible that Ubuntu ignores the translation files, because the language I installed is en-US?

I also installed the Dutch language packs.

And if a repository is not gpg signed, does Ubuntu ignore the gpg file?Sometimes repos will not let you download from them if you don't have a signed gpg signature.  Other times, it will simply warn you about downloading from untrusted sources if your gpg signature is not present.

I suppose your error could be coming from the fact that you're using English and you are trying to download Dutch language packs.

I'm not sure how else to advise you at this point. Sorry. :(

---

