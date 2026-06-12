---
title: "A complete edgy eft sources.list"
date: 2006-11-02
forum: Repositories &amp; Backports
---

### Post by FuzZy2006 on 2006-11-02
Can you post here one as complete as possible sources list? Cos' mine is the default. And the commands to add the key. Or is there a site to create an automatic sources.list like it was for dapper?

---

### Post by zgerrz on 2006-11-02
You can check out this thread here:

[http://www.ubuntuforums.org/showthread.php?t=265326](http://www.ubuntuforums.org/showthread.php?t=265326)

---

### Post by Treviño on 2006-11-06
Just done... [http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)

Please digg it :P

---

### Post by gg234 on 2006-11-07
try here is the [big list of edgy source list ]("http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html")[/

---

### Post by kr0n1x on 2006-11-10
> **gg234 said:**
> try here is the [big list of edgy source list ]("http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html")[/

i can't open the complete article of that link:( i can't get the list!

---

### Post by gg234 on 2006-11-10
> **kr0n1x said:**
> i can't open the complete article of that link:( i can't get the list!

i have just checked and it is working fine

---

### Post by kr0n1x on 2006-11-11
> **gg234 said:**
> i have just checked and it is working fine

can you send me the sources list? or the web page...

---

### Post by Aualin on 2006-11-11
```
Ubuntu Edgy Eft complete sources.list (repository list file)
by Admin @ 9:55 am. Filed under Other Linux

Repositories There are thousands of programs available to install on Ubuntu. These programs are stored in software archives (repositories) and are available for installation over the Internet. This makes it very easy to install new programs. It is also very secure, because each program you install is thoroughly tested and built specifically for Ubuntu.


Here is the List of Ubuntu Edgy Eft Source list

# Use the following sources.list at your own risk.

# Ubuntu Main

deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-proposed main restricted universe multiverse

# Bug fix Updates

deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

# kubuntu.org packages for the latest KDE version

deb http://kubuntu.org/packages/kde-latest edgy main
deb http://kubuntu.org/packages/kde-355 edgy main
deb-src http://kubuntu.org/packages/kde-latest edgy main

GPG Key Information

wget http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg | sudo apt-key add

kubuntu-packages-jriddell-key.gpg

# kubuntu.org packages for the latest Koffice version

deb http://kubuntu.org/packages/koffice-latest edgy main
deb-src http://kubuntu.org/packages/koffice-latest edgy main

GPG Key Information

wget http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg | sudo apt-key add

kubuntu-packages-jriddell-key.gpg

# Ubuntu Security Updates

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

# Backports Repository

deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

# Penguin Liberation Front (packages)

deb http://packages.freecontrib.org/ubuntu/plf edgy-plf free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf edgy-plf free non-free

# Canonical Commercial Repository (Opera,Real Player10.. etc)

deb http://archive.canonical.com/ubuntu edgy-commercial main

# Sevea’s Repository (Multimedia Packages)

deb http://seveas.imbrandon.com/ edgy-seveas extras seveas-meta custom
deb-src http://seveas.imbrandon.com/ edgy-seveas extras seveas-meta custom

GPG Key Information

wget http://seveas.imbrandon.com/1135D466.gpg -O- | sudo apt-key add -

#ntfs-3g Source list

The ntfs-3g is in the universe section of ubuntu, so you’ll need first to enable universe.

If you have an NTFS removable device that you want to mount read/write, add one of this mirror in your /etc/apt/sources.list

deb http://givre.cabspace.com/ubuntu/ edgy main-all
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main-all
deb http://flomertens.keo.in/ubuntu/ edgy main-all

Latest version of the driver

Add one of this mirror in your /etc/apt/sources.list to use it :

deb http://givre.cabspace.com/ubuntu/ edgy main
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main
deb http://flomertens.keo.in/ubuntu/ edgy main

GPG Key Information

Use any one of the following Key

wget http://flomertens.keo.in/ubuntu/givre_key.asc -O- | sudo apt-key add -

wget http://givre.cabspace.com/ubuntu/givre_key.asc -O- | sudo apt-key add -

# Google picasa

deb http://dl.google.com/linux/deb/ stable non-free

# archive.kubuntu.de / archive.czessi.net

deb http://archive.czessi.net/ubuntu edgy main restricted universe multiverse preview
deb-src http://archive.czessi.net/ubuntu edgy main restricted universe multiverse preview

GPG Key Information

wget http://archive.czessi.net/ubuntu/kczessi.gpg | sudo apt-key add kczessi.gpg

# Skype for linux

deb http://download.skype.com/linux/repos/debian/ stable non-free

# Beryl

deb http://ubuntu.beryl-project.org/ edgy main-edgy

GPG Key Information

wget http://ubuntu.beryl-project.org/quinn.key.asc -O - | sudo apt-key add -

# Bleeding Edge Wine Packages

deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main

# Latest Amarok Packages

deb http://kubuntu.org/packages/amarok-144 edgy main

GPG Key Information

wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg | sudo apt-key add

kubuntu-packages-jriddell-key.gpg

# GiFT P2P Network

deb http://apt.cerkinfo.be/ unstable main contrib
deb-src http://apt.cerkinfo.be/ unstable main contrib

GPG Key Information

gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys F00175CA
gpg --armor --export F00175CA | sudo apt-key add -

# Trevino’s Repository (Flash 9 Beta,gnash, and many more)

deb http://3v1n0.tuxfamily.org edgy 3v1n0
deb-src http://3v1n0.tuxfamily.org edgy 3v1n0

GPG Key Information

wget http://3v1n0.tuxfamily.org/EDD1E155.gpg -O- | sudo apt-key add -

#FreeNX Repository

deb http://seveas.theplayboymansion.net/seveas edgy-seveas all
deb-src http://seveas.theplayboymansion.net/seveas edgy-seveas all

GPG Key Information

wget http://seveas.theplayboymansion.net/seveas/1135D466.gpg -O- | sudo apt-key add -

# E-Yagi Consulting Community Repository

deb http://eyagi.bpa.nu/~jamie/ubuntu edgy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu edgy main restricted universe multiverse

GPG Key Information

gpg --recv-keys 0x4B6E7209
gpg --export -a 0x4B6E7209 > Yagisan.asc
sudo apt-key add Yagisan.asc

# Ubuntu Taiwan ubuntu extra repository

deb http://apt.ubuntu.org.tw ubtw/
deb http://apt.ubuntu.org.tw ubtw-testing/

# VoIP Ubuntu packages (Asterisk, ekiga, kphone…)

deb http://pkg-voip.buildserver.net/ubuntu edgy main

# MaXeR (KDE Apps)

deb http://repos.knio.it/ etch main contrib non-free
deb-src http://repos.knio.it/ etch main contrib non-free

or

deb http://repos.knio.it/ testing main contrib non-free
deb-src http://repos.knio.it/ testing main contrib non-free

GPG Key Information

wget http://repos.knio.it/key.asc | sudo apt-key add key.asc

# Quinn’s Compiz Packages - http://xgl.compiz.info/ use any one of the following

deb http://www.beerorkid.com/compiz edgy main-edgy

deb http://media.blutkind.org/xgl/ edgy main-edgy

deb http://compiz-mirror.lupine.me.uk/ edgy main-edgy

deb http://ubuntu.compiz.net/ edgy main-edgy

GPG Key Information (use any one of the following)

wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -

wget http://media.blutkind.org/xgl/quinn.key.asc -O - | sudo apt-key add -

wget http://compiz-mirror.lupine.me.uk/quinn.key.asc -O - | sudo apt-key add -

wget http://ubuntu.compiz.net/quinn.key.asc -O - | sudo apt-key add -

# Subpixel Font rendering packages

deb http://www.elisanet.fi/mlind/ubuntu edgy fonts
deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts

GPG Key Information

gpg --recv-keys 937215FF
gpg --export --armor 937215FF | sudo apt-key add -

# Easycam packages

deb http://blognux.free.fr/debian unstable main

# Audacious

deb http://vdlinux.sourceforge.jp/ experimental audacious
deb-src http://vdlinux.sourceforge.jp/ experimental audacious

# Geole’s Ubuntu Repository

deb http://ubuntu.geole.info/ edgy universe multiverse

GPG Key Information

wget http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg | sudo apt-key add geole-apt-key.gpg

# Samba

deb http://www.linux2go.dk/ubuntu edgy main
deb-src http://www.linux2go.dk/ubuntu edgy main

# GCompris, Televidilo, Kdocker, etc

deb http://thomas.enix.org/pub/debian/packages/ edgy main

# Gauvain Repository

deb http://gauvain.tuxfamily.org/repos edgy contrib
deb-src http://gauvain.tuxfamily.org/repos edgy contrib

# gnomemeeting

deb http://snapshots.ekiga.net/ubuntu/ edgy main
deb-src http://snapshots.ekiga.net/ubuntu/ edgy main
#deb http://snapshots.voxgratia.org/ubuntu/ edgy main
#deb-src http://snapshots.voxgratia.org/ubuntu/ edgy main

GPG Key Information

wget http://snapshots.ekiga.net/cvs/gpgkey/buildd.gpg|apt-key add -

# seb128 repository (gaim - rhythmbox)

deb http://people.ubuntu.com/~seb128/deb ./
deb-src http://people.ubuntu.com/~seb128/deb ./

# MythTV packages

deb http://home.eng.iastate.edu/~superm1 edgy all
deb-src http://home.eng.iastate.edu/~superm1 edgy all

GPG Key Information

wget http://home.eng.iastate.edu/~superm1/80DF6D58.gpg -O- | sudo apt-key add -

# Cafuego’s Edgy Stuff: Broadcom kernel firmwares, google-earth, beagle

deb http://au.ubuntu.cafuego.net edgy-cafuego all
deb-src http://au.ubuntu.cafuego.net edgy-cafuego all

GPG Key Information

wget http://au.ubuntu.cafuego.net/969F3F57.gpg -O- | sudo apt-key add -

# Debuntu Ubuntu edgy packages

deb http://repository.debuntu.org/ edgy multiverse
deb-src http://repository.debuntu.org/ edgy multiverse

GPG Key Information

wget http://repository.debuntu.org/GPG-Key-chantra.txt | sudo apt-key add GPG-Key-chantra.txt

# BMPx Edgy Repository

deb http://files.beep-media-player.org/packages/ubuntu edgy main universe
deb http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/ edgy/
deb-src http://files.beep-media-player.org/packages/ubuntu edgy main universe

GPG Key Information

sudo apt-key add bmp-packages.pubkey

or

sudo apt-key add http://files.beep-media-player.org/packages/bmp-packages.pubkey

# Morgoth Repository (Monkey’s Audio, xmms pugins, vlc plugins, gqview, audacity…)

deb http://morgoth.free.fr/ubuntu edgy-backports main
deb-src http://morgoth.free.fr/ubuntu edgy-backports main

GPG Key Information

sudo apt-key add http://morgoth.free.fr/ubports/dlsignkey.php

# ATi & nVidia drivers Ubuntu packages

For 32 bit

deb http://albertomilone.com/drivers/edgy/nonlegacy/32bit binary/

For 64 bit

deb http://albertomilone.com/drivers/edgy/nonlegacy/64bit binary/

GPG Key Information

wget http://albertomilone.com/drivers/tseliot.asc

gpg –import tseliot.asc

gpg –export –armor albertomilone@alice.it | sudo apt-key add -

#Automatix

deb http://www.getautomatix.com/apt edgy main

GPG Key Information

wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

# SoS: SeerOfSouls

deb http://SeerOfSouls.com/ edgy contrib
deb-src http://SeerOfSouls.com/ edgy contrib

GPG Key Information

wget http://seerofsouls.com/keys/hawkwind.asc | sudo apt-key add hawkwind.asc

# Treviño’s Ubuntu Dapper Repository

# Many “random” software: aMule, amsn, gnash, google-earth, stellarium, moto4lin

deb http://3v1n0.tuxfamily.org edgy 3v1n0
deb-src http://3v1n0.tuxfamily.org edgy 3v1n0

GPG Key Information

wget http://3v1n0.tuxfamily.org/EDD1E155.gpg -O- | sudo apt-key add -

#Candyz’s Ubuntu Packages

for Ubuntu 6.10 (Edgy) - i386

deb http://cle.linux.org.tw/candyz/Ubuntu/edgy i386/

for Ubuntu 6.10 (Edgy) - powerpc

deb http://cle.linux.org.tw/candyz/Ubuntu/edgy ppc/

for Ubuntu 6.10 (Edgy) - amd64

deb http://cle.linux.org.tw/candyz/Ubuntu/edgy amd64/

GPG Key Information

wget http://cle.linux.org.tw/candyz/Ubuntu/candyz.key -O -|sudo apt-key add -

The above source list are mainly for ubuntu edgy if you want to use these source list you need to edit the

/etc/apt/sources.list

sudo gedit /etc/apt/sources.list

add which source list you want to use save and exit the file.

Now you should see some of the source list is having the GPG key information for these keys you need to installed using the command menction against each source list just copy and paste the command in your terminal after finishing this gpg key infomation you need to update the source list using the following command

sudo apt-get update

Now you can install which package you want to install

Now we will see one example how to use these source lists

Example

If you want to install automatix package you need to use the following commands

add the following source list in /etc/apt/sources.list file save and exit

deb http://www.getautomatix.com/apt edgy main

Now you need to run the following commands to import GPG key files

wget http://www.getautomatix.com/apt/key.gpg.asc
gpg –import key.gpg.asc
gpg –export –armor 521A9C7C | sudo apt-key add -

Now you need to update the source list using the following command

sudo apt-get update

Install automatix using the following command

sudo apt-get install automatix2

If you feel some source list is missing from this list you can always suggest that source list

Possible errors

W: GPG error: ftp://mirror.list.net stable Release:
The following signatures couldn’t be verified
because the public key is not available: NO_PUBKEY [key_id]
W: You may want to run apt-get update to correct these problems

You need to make sure that you have imported the corresponding GPG key information

If you want to generate generate an ubuntu sources.list for your preferred set of repositories from here 
```

---

### Post by kr0n1x on 2006-11-11
thanks Aualin, but now also i can read/look the web page ( lol... )

now i have the 3v1n0 sources.list...i need to replace it with sources.list of debianadmin.com?

i think no..you?

---

### Post by BLTicklemonster on 2006-11-12
> **Treviño said:**
> Just done... [http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)

Please digg it :P

I don't think so:

[http://ubuntuforums.org/showthread.php?t=297814](http://ubuntuforums.org/showthread.php?t=297814)

I'm having fits over here fixing stuff.

---

### Post by Aualin on 2006-11-12
you dont need to do that. You can check wich repos debian admin got that trevino hasnt.

---

