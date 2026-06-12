---
title: "Commercial software repository for Dapper"
date: 2007-01-29
forum: Repositories &amp; Backports
---

### Post by zolero on 2007-01-29
This is Ubuntu 6.06 LTS Dapper Drake's Closed Source Repositories.

Canonical, Ubuntu &#8217;s parent company has announced the dapper-commercial repository, where one will 

hopefully find packages released by commercial companies (closed-source) for use by Ubuntu users. You 

read more about this event here:

[http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/](http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/)

This is pretty awesome for us, this means that we can install programs such as Cedega, Real Player, and 

Crossover without having to hunt for them! All you need to do is to add this repository to your sources.list file 

in /etc/apt/sources.list by working around the followings:

Open your ***sources.list*** for editing, by typing in terminal (copy & paste this code):

```
sudo gedit /etc/apt/sources.list
```

You must enter the user password.

The following is the repository line. Copy and paste it into ***sources.list***:

```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

Now save and close it, and then refresh the repositories by typing in terminal:

```
sudo apt-get update
```

That's it. Enjoy the commercial software packages! ;) :lol:

Zolero.

---

### Post by zolero on 2007-09-15
From now on I have a new, much extended repo list on my Dapper. Take a look at it... Perhaps it helps anyone in the community.

Copy/paste it over your sources.list in gedit, then "sudo apt-get update" it and enjoy. I recommend to read its comments carefully. Those contains valuable infos to prevent you from running in troubles... ;-) :-D 8)

 I'm a hungarian language speaker, thus my system runs on that one. For switching to yours native one, change the repos' prefix for example from **deb [http://hu](http://hu). archive...** to **deb [http://es](http://es). archive...** for spanish, and so on. The rest can remain as is.

When you'll use it, have to uncomment the respective line(s) in gedit or eighter graphically with Repositories Manager located in System-Administration-Repository Manager (or something like that). ;-)

```

###################################################################
#   SHOOTER'S CUSTOMIZED REPOSITORY SOURCES LIST - Basic section
#   Ubuntu Server 6.06.1 Dapper Drake - Release i386 2006.08.07-1
#
#   Ubuntu Server 6.06.1 Dapper Drake packages  GPG key: 437D05B5
#
###################################################################

deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb http://hu.archive.ubuntu.com/ubuntu/ dapper main universe multiverse restricted
deb http://hu.archive.ubuntu.com/ubuntu/ dapper-updates main universe multiverse restricted
deb http://hu.archive.ubuntu.com/ubuntu/ dapper-security main universe multiverse restricted
deb http://hu.archive.ubuntu.com/ubuntu/ dapper-proposed main universe multiverse restricted
#deb http://hu.archive.ubuntu.com/ubuntu/ dapper-backports main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu dapper main universe multiverse restricted
deb http://security.ubuntu.com/ubuntu dapper-updates main universe multiverse restricted
deb http://security.ubuntu.com/ubuntu dapper-security main universe multiverse restricted
deb http://security.ubuntu.com/ubuntu dapper-proposed main universe multiverse restricted
#deb http://security.ubuntu.com/ubuntu dapper-backports main universe multiverse restricted

deb-src http://hu.archive.ubuntu.com/ubuntu/ dapper main universe multiverse restricted
deb-src http://hu.archive.ubuntu.com/ubuntu/ dapper-updates main universe multiverse restricted
deb-src http://hu.archive.ubuntu.com/ubuntu/ dapper-security main universe multiverse restricted
deb-src http://hu.archive.ubuntu.com/ubuntu/ dapper-proposed main universe multiverse restricted
#deb-src http://hu.archive.ubuntu.com/ubuntu/ dapper-backports main universe multiverse restricted

deb-src http://security.ubuntu.com/ubuntu dapper main universe multiverse restricted
deb-src http://security.ubuntu.com/ubuntu dapper-updates main universe multiverse restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main universe multiverse restricted
deb-src http://security.ubuntu.com/ubuntu dapper-proposed main universe multiverse restricted
#deb-src http://security.ubuntu.com/ubuntu dapper-backports main universe multiverse restricted

######################################################
#   Canonical Commercial packages - GPG key: 437D05B5
######################################################

#deb http://archive.canonical.com dapper-commercial main

#deb-src http://archive.canonical.com dapper-commercial main


################################################################################################
#   SHOOTER'S CUSTOMIZED REPOSITORY SOURCES LIST - Source-o-matic & kobleraj section
#
#   If you get GPG errors with this sources.list, locate the GPG key in this file
#   and run these commands (where KEY is replaced with the indicated key)
#
#   gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY GOES HERE && gpg --export --armor KEY GOES HERE | sudo apt-key add -
################################################################################################


########################################################
#   Seveas' Ubuntu packages mirrors - GPG key: 1135D466
########################################################

#deb http://mirror.ubuntulinux.nl/ dapper-seveas all
#deb http://seveas.theplayboymansion.net/seveas/ dapper-seveas all

#deb-src http://mirror.ubuntulinux.nl/ dapper-seveas all
#deb-src http://seveas.theplayboymansion.net/seveas/ dapper-seveas all


#######################################
#   Upstream Opera - GPG key: 6A423791
#######################################

#deb http://deb.opera.com/opera etch non-free


#################################################
#   Upstream Wine repository - GPG key: 387EE263
#################################################

#deb http://wine.budgetdedicated.com/apt dapper main

#deb-src http://wine.budgetdedicated.com/apt dapper main


####################################################################################
#   Medibuntu (Multimedia & Entertainment - ex Penguin Liberation Front) repos
#   Report any bug on https://launchpad.net/products/medibuntu/+bugs
#   For gpg trust-signing these packages run the following command in terminal:
#
#   wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
#
#   or you can use alternatively this one (in case of the SOS-STS mirror):
#
#   wget -q http://medibuntu.sos-sts.com/repo/0C5A2783.gpg -O- | sudo apt-key add -
####################################################################################

#deb http://packages.medibuntu.org/ dapper free non-free
#deb http://packages.medibuntu.org/ dapper free non-free

#deb-src http://packages.medibuntu.org/ dapper-staging free non-free
#deb-src http://packages.medibuntu.org/ dapper-staging free non-free

#deb http://medibuntu.sos-sts.com/repo/ dapper free non-free

#deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free


######################################################################################
#   Marillat Debian Multimedia repository. You need to DOWNLOAD AND INSTALL FIRST the
#   signature gpg key. For do this type in terminal:
#
#   sudo apt-get install debian-multimedia-keyring
######################################################################################

#deb http://debian.netcologne.de/debian-multimedia.org stable main
#deb http://debian.netcologne.de/debian-multimedia.org unstable main

#deb-src http://debian.netcologne.de/debian-multimedia.org stable main
#deb-src http://debian.netcologne.de/debian-multimedia.org unstable main


##########################################################################################
#   The latest Beryl repository for Ubuntu. Get the trusted signature from here:
#
#   wget -q http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
#
#   Or use this GPG key alternatively: ed8a569e
##########################################################################################

#deb http://ubuntu.beryl-project.org/ edgy main
#deb http://ubuntu.beryl-project.org/ feisty main


###################################################################################
#   Ubuntu repository for Beryl screenlets - GPG key: F854AFD7
#
#   wget -q http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg -O- | sudo apt-key add -
###################################################################################

#deb http://hendrik.kaju.pri.ee/ubuntu edgy all screenlets
#deb http://hendrik.kaju.pri.ee/ubuntu feisty all screenlets

#deb-src http://hendrik.kaju.pri.ee/ubuntu edgy all screenlets
#deb-src http://hendrik.kaju.pri.ee/ubuntu feisty all screenlets


###################################################################################
#   Ubuntu Dapper backported and new testing packages from University Klagenfurt.
#
#   wget -q http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub -O- | sudo apt-key add -
###################################################################################

#deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper  uniklu-desktop uniklu-intern uniklu-nfsv4 uniklu-testing uniklu-vserver uniklu

#deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper  uniklu-desktop uniklu-intern uniklu-nfsv4 uniklu-testing uniklu-vserver uniklu


###########################################################################################
#   Subpixel font rendering packages with improved fonts on LCDs, and a lot of misc stuffs.
#   WARNING: These packages may violate some patents!!!
#
#   wget -q http://www.telemail.fi/mlind/ubuntu/937215FF.gpg -O- | sudo apt-key add -
###########################################################################################

#deb http://www.telemail.fi/mlind/ubuntu feisty fonts main

#deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts main


####################################################################################
#   Ubuntu system administrator packages (the Compiz suite in the eyecandy section).
#
#   wget -q http://ubuntu.moshen.de/2F306651.gpg -O- | sudo apt-key add -
####################################################################################

#deb http://ubuntu.moshen.de dapper eyecandy misc mono multimedia

#deb-src http://ubuntu.moshen.de dapper eyecandy misc mono multimedia


################################################################################################
#   Treviño&#8217;s bleeding edge software repository: aMule, aMSN, Mercury, flash&#8230; and much more.
#   Further informations and complete packages list can be found at: http://3v1n0.tuxfamily.org
#
#   BE VERY CAREFULL WITH USE OF PACKAGES FROM SUSPEND2 COMPONENT OR ELSE YOU'LL END CRYING!!!
#
#   wget -q http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
#
#   If the key above fails or get errors checkout this one: EDD1E155
################################################################################################

#deb http://download.tuxfamily.org/3v1deb dapper 3v1n0 beryl-svn
#deb http://download.tuxfamily.org/3v1deb edgy 3v1n0 beryl-svn suspend2 xorg-7.2
#deb http://download.tuxfamily.org/3v1deb feisty 3v1n0 eyecandy suspend2

#deb-src http://download.tuxfamily.org/3v1deb dapper 3v1n0 beryl-svn
#deb-src http://download.tuxfamily.org/3v1deb edgy 3v1n0 beryl-svn suspend2 xorg-7.2
#deb-src http://download.tuxfamily.org/3v1deb feisty 3v1n0 eyecandy suspend2


###########################################################################
#   Cinelerra CV edition (http://cv.cinelerra.org) with Ubuntu Feisty.
#
#   NOTE THAT THE ARE UNSIGNED PACKAGES!!!
#
#   This repository is being maintained by Jure Cuhalev (gandalf@owca.info)
#   I will also announce new builds on my blog in category Ubuntu:
#
#   http://www.kiberpipa.org/~gandalf/blog/?cat=11
###########################################################################

#deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./
#deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/ ./
#deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/ ./


######################################################################################
#   Dapper, Edgy, Feisty & Gutsy Debuntu repositories. Gaim, Pidgin, subtitleeditor,
#   unace-nonfree, latest fuse and more.
#
#   Get PGP key with this:
#
#   wget -q http://repository.debuntu.org/GPG-Key-chantra.txt -O- | sudo apt-key add -
######################################################################################

#deb http://repository.debuntu.org/ dapper multiverse
#deb http://repository.debuntu.org/ edgy multiverse
#deb http://repository.debuntu.org/ feisty multiverse
#deb http://repository.debuntu.org/ gutsy multiverse

#deb-src http://repository.debuntu.org/ dapper multiverse
#deb-src http://repository.debuntu.org/ edgy multiverse
#deb-src http://repository.debuntu.org/ feisty multiverse
#deb-src http://repository.debuntu.org/ gutsy multiverse


#####################################################################################
#   Miro & Democracy Player's (plays almost all video formats) repository for Dapper
#   served by PCF Foundation. NO PUBKEY SPECIFIED!!!
#####################################################################################

#deb http://ftp.osuosl.org/pub/pculture.org/Miro/linux/repositories/ubuntu dapper/


###########################################################################
#   Cafuego's Ubuntu Dapper stuffs version 1.0
#
#   wget -q http://debian.cafuego.net/969F3F57.gpg -O- | sudo apt-key add -
###########################################################################

#deb http://ubuntu.cafuego.net/ dapper-cafuego all


################################################################################################
#   Adding repositories with Scribus related packages for Dapper. First is the main repository,
#   second one is a backup mirror. Pubkey is valid for both of them.
#
#   gpg --keyserver subkeys.pgp.net --recv-keys EEF818CF && gpg --armor --export EEF818CF | sudo apt-key add -
################################################################################################

#deb http://debian.scribus.net/debian dapper main non-free
#deb http://debian.tagancha.org/debian dapper main restricted

#deb-src http://debian.scribus.net/debian dapper main non-free
#deb-src http://debian.tagancha.org/debian dapper main non-free


##################################################################################
#   Ubuntu's Givre repository for NTFS-3G and FUSE. Public key is: 6B80D6DA
#   It can be used alternatively one of the mirrors listed hereunder.
#
#   wget -q http://flomertens.keo.in/ubuntu/givre_key.asc -O- | sudo apt-key add -
##################################################################################

#deb http://flomertens.keo.in/ubuntu/ dapper main
#deb http://givre.cabspace.com/ubuntu/ dapper main
#deb http://ntfs-3g.sitesweetsite.info/ubuntu/ dapper main

#deb-src http://flomertens.keo.in/ubuntu/ dapper main
#deb-src http://givre.cabspace.com/ubuntu/ dapper main
#deb-src http://ntfs-3g.sitesweetsite.info/ubuntu/ dapper main


################################################################################################
#   Geole&#8217;s Ubuntu Repository
#
#   wget -q http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg | sudo apt-key add geole-apt-key.gpg
################################################################################################

#deb http://ubuntu.geole.info/ edgy main universe multiverse


######################################################################################
#   MythTV Repository for Dapper Ubuntu Linux
#
#   wget -q http://home.eng.iastate.edu/~superm1/80DF6D58.gpg -O- | sudo apt-key add -
######################################################################################

#deb http://home.eng.iastate.edu/~superm1 dapper all

#deb-src http://home.eng.iastate.edu/~superm1 dapper all


#####################################################################################
#   Morgoth repository (Monkey&#8217;s Audio, xmms pugins, vlc plugins, gqview, audacity&#8230;)
#
#   wget -q http://morgoth.free.fr/ubports/dlsignkey.php -O- | sudo apt-key add
#####################################################################################

#deb http://morgoth.free.fr/ubuntu edgy-backports main

#deb-src http://morgoth.free.fr/ubuntu edgy-backports main


#########################################################################################
#   SoS: Seer Of Souls repository
#
#   wget -q http://seerofsouls.com/keys/hawkwind.asc -O- | sudo apt-key add hawkwind.asc
#########################################################################################

#deb http://seerofsouls.com/ edgy contrib

#deb-src http://seerofsouls.com/ edgy contrib


######################################################################################
#   Candyz's Ubuntu Dapper APT repository
#
#   wget -q http://cle.linux.org.tw/candyz/Ubuntu/candyz.key -O- | sudo apt-key add -
######################################################################################

#deb http://cle.linux.org.tw/candyz/Ubuntu/dapper i386/


########################################################################################
#   InitNG (New Generation) Debian/Ubuntu repository for Dapper Drake.
#   EXPLANATION: This is a very new, usefull, and nice tool which improves your machine
#   boot-up process' speed, by running scripts and things asynchronously.
#
#   WARNING: InitNG is beta software, and must be used with caution. However, it can be
#   installed side-by-side with init. It is recommended that you duplicate the relevant
#   blocks of your bootloader by copying configuration before add the changes. 
#
#   gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 77AFC5B7 && gpg --armor --export 77AFC5B7 | sudo apt-key add -
########################################################################################

#deb http://debian.space-based.de/debs/ experimental main

#deb-src http://debian.space-based.de/debs/ experimental main


#############################################################################################
#   The latest VLC VideoLAN repository (with libraries and plugins) from the project website.
#
#   No need for pubkey, but you have to install first VLC VideoLAN from normal universe repo,
#   then update using this one (uncomment and "sudo apt-get update" it).
#############################################################################################

#deb ftp://ftp.videolan.org/pub/videolan/ubuntu/ dapper universe

#deb-src ftp://ftp.videolan.org/pub/videolan/ubuntu/ dapper universe


##################################################################################
#   Asher256's miscelo software repository for Dapper Drake. No pubkey provided!!!
##################################################################################

#deb http://asher256-repository.tuxfamily.org dapper main dupdate french


#######################################################
#   END OF SHOOTER'S REPOSITORIES SOURCES.LIST FILE   #
#######################################################

```

---

