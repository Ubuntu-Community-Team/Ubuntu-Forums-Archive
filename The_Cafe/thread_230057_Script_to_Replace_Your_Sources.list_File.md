---
title: "Script to Replace Your Sources.list File"
date: 2006-08-05
forum: The Cafe
---

### Post by Christmas on 2006-08-05
I just made this small script to replace the sources.list file. It's intended for newbies so they just run it and have the sources replaced, without any manual configuration.
```

#!/bin/bash

# Copyright (C) 2006 Craciun Dan
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
# or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License
# for more details.
#
# You should have received a copy of the GNU General Public License along
# with this program; if not, write to the Free Software Foundation, Inc., 51
# Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA

echo "A TLD (Top Level Domain) is a two-letter country code that defines the last two letters of a website's name located in that country."
echo "For example, the United States' TLD is US, Germany's TLD is DE etc."
echo "Please enter your country's TLD (lowercase letters only):"
read tld
count=1
while [ $count = 1 ]
do
if   [ $tld = "at" ]
then
	count=0
elif [ $tld = "ca" ]
then
	count=0
elif [ $tld = "ch" ]
then
	count=0
elif [ $tld = "de" ]
then
	count=0
elif [ $tld = "es" ]
then
	count=0
elif [ $tld = "fi" ]
then
	count=0
elif [ $tld = "fr" ]
then
	count=0
elif [ $tld = "gb" ]
then
	count=0
elif [ $tld = "gr" ]
then
	count=0
elif [ $tld = "in" ]
then
	count=0
elif [ $tld = "it" ]
then
	count=0
elif [ $tld = "no" ]
then
	count=0
elif [ $tld = "nz" ]
then
	count=0
elif [ $tld = "pl" ]
then
	count=0
elif [ $tld = "ro" ]
then
	count=0
elif [ $tld = "ru" ]
then
	count=0
elif [ $tld = "se" ]
then
	count=0
elif [ $tld = "us" ]
then
	count=0
else
	count=1
	echo "The TLD you entered is not valid or there are no sources available for it."
	echo "Please enter your country's TLD (lowercase letters only):"
	read tld
fi
done
if [ $count = 0 ]
then
	if test -f sources.list_tmp
	then
		rm sources.list_tmp
	fi
	echo "Replacing your sources with the Romanian ones..."
	echo "# Ubuntu Supported Packages (GPG Key: 437D05B5)" >> sources.list_tmp
	echo "deb http://$tld.archive.ubuntu.com/ubuntu dapper main restricted" >> sources.list_tmp
	echo "deb http://$tld.archive.ubuntu.com/ubuntu dapper-updates main restricted" >> sources.list_tmp
	echo "deb http://security.ubuntu.com/ubuntu dapper-security main restricted" >> sources.list_tmp
	echo "" >> sources.list_tmp
	echo "# Ubuntu Community Supported Packages (GPG Key: 437D05B5)" >> sources.list_tmp
	echo "deb http://$tld.archive.ubuntu.com/ubuntu dapper universe multiverse" >> sources.list_tmp
	echo "deb http://$tld.archive.ubuntu.com/ubuntu dapper-updates universe multiverse" >> sources.list_tmp
	echo "deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse" >> sources.list_tmp
	echo "" >> sources.list_tmp
	echo "# Ubuntu Commercial Packages" >> sources.list_tmp
	echo "deb http://archive.canonical.com/ubuntu dapper-commercial main" >> sources.list_tmp
	echo "You may be required to enter your user's password."
	sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
	sudo cp sources.list_tmp /etc/apt/sources.list
	rm sources.list_tmp
	sudo aptitude update
fi
```
I made it also available for download including a README file on my site, [here]("http://86.104.196.200/scripts/repositories_0.3.tar.gz"). I'll also add some more countries, but at the moment you can manually modify it. 
Just add this piece of code:
```
elif [ $tld = "TLD" ]
then
	count=0
```
under this:
```

if   [ $tld = "at" ]
then
	count=0

```
replacing "TLD" with your country's TLD. Still a newbie to Bash scripting so please sent me feedback, maybe it could get shorter?
This piece of code
```
 if [ $tld = "at" || $tld = "ro" || etc... ]
```
doesn't work.

So what do you think?

---

### Post by Titus A Duxass on 2006-08-05
Nice but is it necessary.
Editting files is one of the base steps of getting to know linux.  By automising a simple task you are taking away the opportunity of learning (even if it is sometimes learning by mistakes), still it is a nice idea.

---

### Post by Christmas on 2006-08-05
You are right about the need of learning, I myself agree with it, but there are persons who don't like doing all that stuff manually. Also, it is a fast way of doing it (you can also have a backup and copy it over -- which is more faster even) but it provides repos for more that one country, depending on your choice.

---

### Post by Johan! on 2006-08-05
What´s wrong with [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")?

It works great, and you can customize it too.

---

### Post by richbarna on 2006-08-05
> **Christmas said:**
> I just made this small script to replace the sources.list file. It's intended for newbies so they just run it and have the sources replaced, without any manual configuration.


So what do you think?

I just gave it a go and it works. (I didn't have to chmod by the way)

In your "Readme" you didn't tell the new users how to extract the tar.gz archive or that they have to "cd" to the directory first.

I see that there is no option to leave off the country code, there are sources.lists without the country prefix.

Also you have the Konsole in the guide but not the Terminal, and the repos are Ubuntu not Kubuntu.

Here is a mixed (both ubuntu and kubuntu) sources list for you to look at :-

> [FONT=courier new,courier] 
# If you get errors about missing keys, lookup the key in this file
       # and run these commands (replace KEY with the key number)
       #
       # gpg –keyserver subkeys.pgp.net –recv KEY
       # gpg –export –armor KEY | sudo apt-key add - 	[/FONT][FONT=courier new,courier]             # Ubuntu supported packages (packages, GPG key: 437D05B5)
       deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
       deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
       deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Ubuntu supported packages (sources, GPG key: 437D05B5)
       deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
       deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
       deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Ubuntu community supported packages (packages, GPG key: 437D05B5)
       deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
       deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
       deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Ubuntu community supported packages (sources, GPG key: 437D05B5)
       deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
       deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
       deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Ubuntu backports project (packages, GPG key: 437D05B5)
       deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Ubuntu backports project (sources, GPG key: 437D05B5)
       deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse[/FONT]
 	[LEFT] [/LEFT]
 	[LEFT][FONT=courier new,courier]# CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
# RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main 	[/FONT][FONT=courier new,courier]  # Seveas’ packages (packages, GPG key: 1135D466)
       deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas all[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Seveas’ packages (sources, GPG key: 1135D466)
       deb-src [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas all[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
       deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
       deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
       deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
       deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main
deb [http://kubuntu.org/packages/kde-354](http://kubuntu.org/packages/kde-354) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
       deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
       deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
       deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
       deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Bleeding edge wine packages (packages)
       deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Bleeding edge wine packages (sources)
       deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # The Opera browser (packages)
       deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Penguin Liberation Front (packages)
       #deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free
       deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Penguin Liberation Front (sources)
       #deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free
       deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  ## archive.kubuntu.de / archive.czessi.net
       # The repository from Kubuntu Germany
       # wget [http://archive.czessi.net/ubuntu/kczessi.gpg](http://archive.czessi.net/ubuntu/kczessi.gpg)
       # sudo apt-key add kczessi.gpg
       deb [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) dapper main restricted universe multiverse preview 
       deb-src [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) dapper main restricted universe multiverse preview[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Amarok 1.4 Packages
       deb [http://kubuntu.org/packages/amarok-14](http://kubuntu.org/packages/amarok-14) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # KDE 3.5.3 Packages
       deb [http://kubuntu.org/packages/kde-353](http://kubuntu.org/packages/kde-353) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # KOffice 1.5.1 Packages
  deb [http://kubuntu.org/packages/koffice-151](http://kubuntu.org/packages/koffice-151) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  ## Doomsday games
       #deb [http://eyagi.bpa.nu/~jamie/ubuntu](http://eyagi.bpa.nu/~jamie/ubuntu) dapper main restricted universe multiverse
       #deb-src [http://eyagi.bpa.nu/~jamie/ubuntu](http://eyagi.bpa.nu/~jamie/ubuntu) dapper main restricted universe multiverse
             # Dev not-public (Breezy Packages)
       deb [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free
       deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Achim’s Unofficial ‘dapper’ Kubuntu packages
       deb [http://www.mpe.mpg.de/~ach/kubuntu/dapper](http://www.mpe.mpg.de/~ach/kubuntu/dapper) ./
       deb-src [http://www.mpe.mpg.de/~ach/kubuntu/dapper](http://www.mpe.mpg.de/~ach/kubuntu/dapper) ./[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Ubuntu Taiwan ubuntu extra repository
       deb [http://apt.ubuntu.org.tw](http://apt.ubuntu.org.tw) ubtw/
       deb [http://apt.ubuntu.org.tw](http://apt.ubuntu.org.tw) ubtw-testing/[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Ubuntu dapper University Klagenfurt packages
       # $ wget [http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub](http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub)
       # $ sudo apt-key add uniklu-debuild.pub 
       #   uniklu:         backports and new packages   
       #   uniklu-desktop: packages for uniklu desktop
       #   uniklu-intern:  not freely redistributable (jvm), or modified packages
       #   uniklu-nfsv4:   nfsv4 kernel and packages
       #   uniklu-vserver: vserver kernel
       #   uniklu-testing: packages not ready for general use !
       deb     [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  dapper  uniklu
       deb     [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  dapper  uniklu-desktop
       deb     [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  dapper  uniklu-intern
       deb     [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  dapper  uniklu-nfsv4
       deb     [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  dapper  uniklu-vserver
       deb     [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  dapper  uniklu-testing
       deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  dapper  uniklu
       deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  dapper  uniklu-desktop
       deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  dapper  uniklu-intern
       deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  dapper  uniklu-nfsv4
       deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  dapper  uniklu-vserver
       deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/)  dapper  uniklu-testing[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Ekiga and Debian pkg-voip
       deb [http://pkg-voip.buildserver.net/ubuntu](http://pkg-voip.buildserver.net/ubuntu) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # VLC nightlies
       deb [http://nightlies.videolan.org/build/dapper-i386](http://nightlies.videolan.org/build/dapper-i386) /[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # # MaXeR (KDE Apps)
       # # deb [http://repos.knio.it/](http://repos.knio.it/) sarge main contrib non-free
       # # deb-src [http://repos.knio.it/](http://repos.knio.it/) sarge main contrib non-free
       # deb [http://repos.knio.it/](http://repos.knio.it/) breezy main contrib non-free
       # deb-src [http://repos.knio.it/](http://repos.knio.it/) breezy main contrib non-free[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]             # Quinn’s Compiz Packages - [http://xgl.compiz.info/](http://xgl.compiz.info/)
       deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
       deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
       deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # CompizTool package
       deb [http://compiztools.free.fr/debian](http://compiztools.free.fr/debian) unstable main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Wormux - Worm Clone packages
       deb [http://download.gna.org/wormux/debs](http://download.gna.org/wormux/debs) dapper/[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Skype packages
       deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Easycam packages
       deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Audacious
       deb [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious
       deb-src [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Listen
       deb [http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/)    ./[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # BMPx
       deb [http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/](http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/) dapper/[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Freevo
       # wget [http://www.geole.de/fileadmin/data/misc/geole-apt-key.gpg](http://www.geole.de/fileadmin/data/misc/geole-apt-key.gpg)
       # sudo apt-key add geole-apt-key.gpg
       deb [http://ubuntu.geole.de/](http://ubuntu.geole.de/) dapper universe multiverse[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Samba
       deb [http://www.linux2go.dk/ubuntu](http://www.linux2go.dk/ubuntu) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # GCompris, Televidilo, Kdocker,…
       deb [http://thomas.enix.org/pub/debian/packages/](http://thomas.enix.org/pub/debian/packages/) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Asher256’s Repository
       deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) breezy main dupdate french
       deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Gauvain Repository
       deb [http://gauvain.tuxfamily.org/repos](http://gauvain.tuxfamily.org/repos) dapper contrib
       deb-src [http://gauvain.tuxfamily.org/repos](http://gauvain.tuxfamily.org/repos) dapper contrib[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Tvfreeplayer Packages
       deb [http://www.tvfreeplayer.com/linux/ubuntu/dapper/](http://www.tvfreeplayer.com/linux/ubuntu/dapper/) unstable main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # gnomemeeting (ekiga)
       deb [http://snapshots.gnomemeeting.net/ubuntu/](http://snapshots.gnomemeeting.net/ubuntu/) dapper main
       deb-src [http://snapshots.gnomemeeting.net/ubuntu/](http://snapshots.gnomemeeting.net/ubuntu/) dapper main
       deb [http://snapshots.voxgratia.org/ubuntu/](http://snapshots.voxgratia.org/ubuntu/) dapper main
       deb-src [http://snapshots.voxgratia.org/ubuntu/](http://snapshots.voxgratia.org/ubuntu/) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # seb128 repository (gaim - rhythmbox)
       deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  ## lprod packages: many audio/video apps: avidemux, cinelerra… (breezy partly working on dapper)
       # deb [http://lprod.org/deb/breezy/](http://lprod.org/deb/breezy/) ./[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # Mjpegtools and Cinelerra packages (choose your arch)
  deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
  deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./
  # deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./
  # deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/) ./[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]# LiVes dapper package
deb [http://people.ubuntubrasil.org/~rclbelem/lives/dapper/](http://people.ubuntubrasil.org/~rclbelem/lives/dapper/) ./binary/[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # A little too quiet
       deb [http://apt.alittletooquiet.net/staging](http://apt.alittletooquiet.net/staging) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  # MythTV 0.19
  deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
  deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]  ## SimplyMepis packages (distro based on k-ubuntu) but different kernel
  # deb [http://apt.mepis.org/6.0/](http://apt.mepis.org/6.0/) mepis main[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]# Cafuego’s Dapper Stuff: Broadcom kernel firmwares, google-earth, beagle… [/FONT][FONT=courier new,courier](GPG key: 969F3F57)[/FONT]
[FONT=courier new,courier]deb [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) dapper-cafuego all bcm43xx
deb-src [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) dapper-cafuego all bcm43xx[/FONT]
 [FONT=courier new,courier]	[/FONT][FONT=courier new,courier]## Ubuntu Dapper Sw-Suspend2 repository - warning: new patched kernel
  [/FONT]
[/LEFT]
 	[LEFT][FONT=courier new,courier]# deb [http://dagobah.ucc.asn.au/ubuntu-suspend2](http://dagobah.ucc.asn.au/ubuntu-suspend2) dapper/ 	[/FONT][FONT=courier new,courier]# Debuntu Ubuntu dapper packages[/FONT] 
[/LEFT]
 	[LEFT][FONT=courier new,courier]# GPG Key-flie: wget [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt)[/FONT][/LEFT]
 	[LEFT][FONT=courier new,courier]deb [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse 	[/FONT][FONT=courier new,courier]# BMPx Dapper Repository
# GPG key-file: [http://files.beep-media-player.org/packages/bmp-packages.pubkey](http://files.beep-media-player.org/packages/bmp-packages.pubkey)
deb [http://files.beep-media-player.org/packages/ubuntu](http://files.beep-media-player.org/packages/ubuntu) dapper main universe
deb-src [http://files.beep-media-player.org/packages/ubuntu](http://files.beep-media-player.org/packages/ubuntu) dapper main universe[/FONT]
[/LEFT]


Nice work, maybe you could make a right click "save as" "double-click" executable. That would be really easy for the new users.

---

### Post by Christmas on 2006-08-05
[quote=richbarna]I just gave it a go and it works. (I didn't have to chmod by the way)

In your "Readme" you didn't tell the new users how to extract the tar.gz archive or that they have to "cd" to the directory first.

I see that there is no option to leave off the country code, there are sources.lists without the country prefix.

Also you have the Konsole in the guide but not the Terminal, and the repos are Ubuntu not Kubuntu.[/quote]
I will make some more indications in the README file, including the extraction of the archive. Also, I'll add more repositories, I was thinking that this ones are widely used and contain almost everything (except for of course latest versions of apps, which always confuse the newbie and could make it run into trouble). They are the "universal" ones. If I add some of the extra repos (like the latest KDE) I'll also have to make some short documentation about them. Thanks a lot for your sources.list file, I guess I'm going to use some of them in the following versions.
[quote=Johan!]What´s wrong with [http://www.ubuntulinux.nl/source-o-matic?](http://www.ubuntulinux.nl/source-o-matic?)

It works great, and you can customize it too.[/quote]
It is indeed great, actually I used it to see how it works (as I'm myself a newbie I wanted to know if the main/universe/multiverse repos are the same for each country, just the TLD is different). 
If I didn't mention already, it's just an alternative which I enjoyed making, you can use the Sources.list Generator as well or any other replaces for it.

Thanks for your feedback.

---

### Post by Christmas on 2006-08-05
Ok I added the Skype repository and also I made an option to generate the default sources if you enter "none" instead of the TLD. I didn't explained in the README how to uncompress it because it makes no sense (I guess if you are reading the README it means you uncrompressed it, right?) but I put the command on the site.

I won't paste the script again, just download it from [here]("http://86.104.196.200/scripts/repositories_0.3.1.tar.gz") and tell me what you think.

---

