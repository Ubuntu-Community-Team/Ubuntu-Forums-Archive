---
title: "Repository Problem in Ubuntu Server?"
date: 2011-02-19
forum: Server Platforms
---

### Post by ljw5491 on 2011-02-19
In Ubuntu Server 10.10, I am trying to use apt-get install to obtain packages, and I keep getting the message "E:  Unable to locate package xyz"  For instance, I tried this with nmap (plug nmap in for xyz)  Is something wrong with my repositories?  Here is my /etc/apt/sources.list:


#
# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted

#deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

---

### Post by cariboo on 2011-02-19
I run lucid on my server, and it looks the same except for lucid instead of maverick. Have you updated the list?

I personally prefer aptitude over apt-get, so I'd use:

```
sudo aptitude update
```

the same command using apt-get:

```
sudo apt-get update
```

---

### Post by elico on 2011-02-19
yes you are missing something
use this site
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
to build your sources list.

---

### Post by nathatanu0 on 2012-01-15
after the command:

sudo apt-get update -qq

I get these:

-------------------------------------------------------------------------------------------------------------------------------
"Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dtp@tifr:~$ sudo apt-get update -qq
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could  not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gp](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gp) g  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release). gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release). gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/Rele](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Rele) ase.gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://mirror.ubuntulinux.nl/dists/dapper-seveas/Release.gpg](http://mirror.ubuntulinux.nl/dists/dapper-seveas/Release.gpg)  Co uld not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://mirror3.ubuntulinux.nl/dists/dapper-seveas/Release.gpg](http://mirror3.ubuntulinux.nl/dists/dapper-seveas/Release.gpg)  C ould not resolve 'netmon.iitb.ac.in'
Failed to fetch [ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release.gp](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release.gp) g  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/kde-latest/dists/dapper/Release.gpg](http://kubuntu.org/packages/kde-latest/dists/dapper/Release.gpg)  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/kde-354/dists/dapper/Release.gpg](http://kubuntu.org/packages/kde-354/dists/dapper/Release.gpg)  Co uld not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/koffice-latest/dists/dapper/Release](http://kubuntu.org/packages/koffice-latest/dists/dapper/Release). gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/amarok-latest/dists/dapper/Release.g](http://kubuntu.org/packages/amarok-latest/dists/dapper/Release.g) pg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg](http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg)  Co uld not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://deb.opera.com/opera/dists/etch/Release.gpg](http://deb.opera.com/opera/dists/etch/Release.gpg)  Could not res olve 'netmon.iitb.ac.in'
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release). gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.czessi.net/ubuntu/dists/dapper/Release.gpg](http://archive.czessi.net/ubuntu/dists/dapper/Release.gpg)  Could  not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/amarok-14/dists/dapper/Release.gpg](http://kubuntu.org/packages/amarok-14/dists/dapper/Release.gpg) Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/kde-353/dists/dapper/Release.gpg](http://kubuntu.org/packages/kde-353/dists/dapper/Release.gpg)  Co uld not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/koffice-151/dists/dapper/Release.gpg](http://kubuntu.org/packages/koffice-151/dists/dapper/Release.gpg)   Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/dists](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/dists) /breezy/Release.gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://www.mpe.mpg.de/~ach/kubuntu/dapper/./Release.gpg](http://www.mpe.mpg.de/~ach/kubuntu/dapper/./Release.gpg)  Could n ot resolve 'netmon.iitb.ac.in'
Failed to fetch [http://apt.ubuntu.org.tw/ubtw/Release.gpg](http://apt.ubuntu.org.tw/ubtw/Release.gpg)  Could not resolve 'ne tmon.iitb.ac.in'
Failed to fetch [http://apt.ubuntu.org.tw/ubtw-testing/Release.gpg](http://apt.ubuntu.org.tw/ubtw-testing/Release.gpg)  Could not res olve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/Release.g](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/Release.g) pg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://pkg-voip.buildserver.net/ubuntu/dists/dapper/Release.gpg](http://pkg-voip.buildserver.net/ubuntu/dists/dapper/Release.gpg)  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://nightlies.videolan.org/build/dapper-i386/Release.gpg](http://nightlies.videolan.org/build/dapper-i386/Release.gpg)  Cou ld not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/Release.gpg](http://www.beerorkid.com/compiz/dists/dapper/Release.gpg)  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://xgl.compiz.info/dists/dapper/Release.gpg](http://xgl.compiz.info/dists/dapper/Release.gpg)  Could not resol ve 'netmon.iitb.ac.in'
Failed to fetch [http://compiztools.free.fr/debian/dists/unstable/Release.gpg](http://compiztools.free.fr/debian/dists/unstable/Release.gpg)  Co uld not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://download.gna.org/wormux/debs/dapper/Release.gpg](http://download.gna.org/wormux/debs/dapper/Release.gpg)  Could no t resolve 'netmon.iitb.ac.in'
Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/Releas](http://download.skype.com/linux/repos/debian/dists/stable/Releas) e.gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://blognux.free.fr/debian/dists/unstable/Release.gpg](http://blognux.free.fr/debian/dists/unstable/Release.gpg)  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://vdlinux.sourceforge.jp/dists/experimental/Release.gpg](http://vdlinux.sourceforge.jp/dists/experimental/Release.gpg)  Co uld not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://theli.free.fr/packages/dapper/./Release.gpg](http://theli.free.fr/packages/dapper/./Release.gpg)  Could not re solve 'netmon.iitb.ac.in'
Failed to fetch [http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/dapper/Release](http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/dapper/Release) .gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.geole.de/dists/dapper/Release.gpg](http://ubuntu.geole.de/dists/dapper/Release.gpg)  Could not resol ve 'netmon.iitb.ac.in'
Failed to fetch [http://www.linux2go.dk/ubuntu/dists/dapper/Release.gpg](http://www.linux2go.dk/ubuntu/dists/dapper/Release.gpg)  Could no t resolve 'netmon.iitb.ac.in'
Failed to fetch [http://thomas.enix.org/pub/debian/packages/dists/dapper/Release](http://thomas.enix.org/pub/debian/packages/dists/dapper/Release). gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/breezy/Release.gp](http://asher256-repository.tuxfamily.org/dists/breezy/Release.gp) g  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/ubuntu/Release.gp](http://asher256-repository.tuxfamily.org/dists/ubuntu/Release.gp) g  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://gauvain.tuxfamily.org/repos/dists/dapper/Release.gpg](http://gauvain.tuxfamily.org/repos/dists/dapper/Release.gpg)  Cou ld not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://www.tvfreeplayer.com/linux/ubuntu/dapper/dists/unstable/R](http://www.tvfreeplayer.com/linux/ubuntu/dapper/dists/unstable/R) elease.gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://snapshots.gnomemeeting.net/ubuntu/dists/dapper/Release.gp](http://snapshots.gnomemeeting.net/ubuntu/dists/dapper/Release.gp) g  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://snapshots.voxgratia.org/ubuntu/dists/dapper/Release.gpg](http://snapshots.voxgratia.org/ubuntu/dists/dapper/Release.gpg) Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://people.ubuntu.com/~seb128/deb/./Release.gpg](http://people.ubuntu.com/~seb128/deb/./Release.gpg)  Could not re solve 'netmon.iitb.ac.in'
Failed to fetch [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/./Rel](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/./Rel) ease.gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/). /Release.gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://people.ubuntubrasil.org/~rclbelem/lives/dapper/./binary/R](http://people.ubuntubrasil.org/~rclbelem/lives/dapper/./binary/R) elease.gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://apt.alittletooquiet.net/staging/dists/dapper/Release.gpg](http://apt.alittletooquiet.net/staging/dists/dapper/Release.gpg)  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://home.eng.iastate.edu/~superm1/dists/dapper/Release.gpg](http://home.eng.iastate.edu/~superm1/dists/dapper/Release.gpg)  C ould not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.cafuego.net/dists/dapper-cafuego/Release.gpg](http://ubuntu.cafuego.net/dists/dapper-cafuego/Release.gpg)  Coul d not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://repository.debuntu.org/dists/dapper/Release.gpg](http://repository.debuntu.org/dists/dapper/Release.gpg)  Could no t resolve 'netmon.iitb.ac.in'
Failed to fetch [http://files.beep-media-player.org/packages/ubuntu/dists/dapper/](http://files.beep-media-player.org/packages/ubuntu/dists/dapper/) Release.gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://3v1n0.tuxfamily.org/dists/dapper/Release.gpg](http://3v1n0.tuxfamily.org/dists/dapper/Release.gpg)  Could not r esolve 'netmon.iitb.ac.in'
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/dapper-backports/Rel](http://old-releases.ubuntu.com/ubuntu/dists/dapper-backports/Rel) ease.gpg  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/main](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main) /binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://mirror.ubuntulinux.nl/dists/dapper-seveas/all/binary-i386](http://mirror.ubuntulinux.nl/dists/dapper-seveas/all/binary-i386) /Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://mirror3.ubuntulinux.nl/dists/dapper-seveas/all/source/Sou](http://mirror3.ubuntulinux.nl/dists/dapper-seveas/all/source/Sou) rces.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/binar](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/binar) y-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/kde-latest/dists/dapper/main/binary-](http://kubuntu.org/packages/kde-latest/dists/dapper/main/binary-) i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/kde-latest/dists/dapper/main/source/](http://kubuntu.org/packages/kde-latest/dists/dapper/main/source/) Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/kde-354/dists/dapper/main/binary-i38](http://kubuntu.org/packages/kde-354/dists/dapper/main/binary-i38) 6/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/koffice-latest/dists/dapper/main/bin](http://kubuntu.org/packages/koffice-latest/dists/dapper/main/bin) ary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/koffice-latest/dists/dapper/main/sou](http://kubuntu.org/packages/koffice-latest/dists/dapper/main/sou) rce/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/amarok-latest/dists/dapper/main/bina](http://kubuntu.org/packages/amarok-latest/dists/dapper/main/bina) ry-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/amarok-latest/dists/dapper/main/sour](http://kubuntu.org/packages/amarok-latest/dists/dapper/main/sour) ce/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/amarok-14/dists/dapper/main/binary-i](http://kubuntu.org/packages/amarok-14/dists/dapper/main/binary-i) 386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-i38](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-i38) 6/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://deb.opera.com/opera/dists/etch/non-free/binary-i386/Packa](http://deb.opera.com/opera/dists/etch/non-free/binary-i386/Packa) ges.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/bin](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/bin) ary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.czessi.net/ubuntu/dists/dapper/main/binary-i386/P](http://archive.czessi.net/ubuntu/dists/dapper/main/binary-i386/P) ackages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/dists](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/dists) /breezy/free/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://www.mpe.mpg.de/~ach/kubuntu/dapper/./Packages.gz](http://www.mpe.mpg.de/~ach/kubuntu/dapper/./Packages.gz)  Could n ot resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu/bi](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu/bi) nary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://pkg-voip.buildserver.net/ubuntu/dists/dapper/main/binary-](http://pkg-voip.buildserver.net/ubuntu/dists/dapper/main/binary-) i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://nightlies.videolan.org/build/dapper-i386/Packages.gz](http://nightlies.videolan.org/build/dapper-i386/Packages.gz)  Cou ld not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Pa](http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Pa) ckages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz](http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz)   Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://compiztools.free.fr/debian/dists/unstable/main/binary-i38](http://compiztools.free.fr/debian/dists/unstable/main/binary-i38) 6/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://download.gna.org/wormux/debs/dapper/Packages.gz](http://download.gna.org/wormux/debs/dapper/Packages.gz)  Could no t resolve 'netmon.iitb.ac.in'
Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-fr](http://download.skype.com/linux/repos/debian/dists/stable/non-fr) ee/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://blognux.free.fr/debian/dists/unstable/main/binary-i386/Pa](http://blognux.free.fr/debian/dists/unstable/main/binary-i386/Pa) ckages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://vdlinux.sourceforge.jp/dists/experimental/audacious/binar](http://vdlinux.sourceforge.jp/dists/experimental/audacious/binar) y-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://theli.free.fr/packages/dapper/./Packages.gz](http://theli.free.fr/packages/dapper/./Packages.gz)  Could not re solve 'netmon.iitb.ac.in'
Failed to fetch [http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/dapper/Package](http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/dapper/Package) s.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.geole.de/dists/dapper/universe/binary-i386/Package](http://ubuntu.geole.de/dists/dapper/universe/binary-i386/Package) s.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://www.linux2go.dk/ubuntu/dists/dapper/main/binary-i386/Pack](http://www.linux2go.dk/ubuntu/dists/dapper/main/binary-i386/Pack) ages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://thomas.enix.org/pub/debian/packages/dists/dapper/main/bin](http://thomas.enix.org/pub/debian/packages/dists/dapper/main/bin) ary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://gauvain.tuxfamily.org/repos/dists/dapper/contrib/binary-i](http://gauvain.tuxfamily.org/repos/dists/dapper/contrib/binary-i) 386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://www.tvfreeplayer.com/linux/ubuntu/dapper/dists/unstable/m](http://www.tvfreeplayer.com/linux/ubuntu/dapper/dists/unstable/m) ain/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://snapshots.gnomemeeting.net/ubuntu/dists/dapper/main/binar](http://snapshots.gnomemeeting.net/ubuntu/dists/dapper/main/binar) y-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://snapshots.voxgratia.org/ubuntu/dists/dapper/main/binary-i](http://snapshots.voxgratia.org/ubuntu/dists/dapper/main/binary-i) 386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://people.ubuntu.com/~seb128/deb/./Packages.gz](http://people.ubuntu.com/~seb128/deb/./Packages.gz)  Could not re solve 'netmon.iitb.ac.in'
Failed to fetch [http://people.ubuntubrasil.org/~rclbelem/lives/dapper/./binary/P](http://people.ubuntubrasil.org/~rclbelem/lives/dapper/./binary/P) ackages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://apt.alittletooquiet.net/staging/dists/dapper/main/binary-](http://apt.alittletooquiet.net/staging/dists/dapper/main/binary-) i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://home.eng.iastate.edu/~superm1/dists/dapper/main/binary-i3](http://home.eng.iastate.edu/~superm1/dists/dapper/main/binary-i3) 86/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.cafuego.net/dists/dapper-cafuego/all/binary-i386/P](http://ubuntu.cafuego.net/dists/dapper-cafuego/all/binary-i386/P) ackages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://repository.debuntu.org/dists/dapper/multiverse/binary-i38](http://repository.debuntu.org/dists/dapper/multiverse/binary-i38) 6/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://files.beep-media-player.org/packages/ubuntu/dists/dapper/](http://files.beep-media-player.org/packages/ubuntu/dists/dapper/) main/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/binary-i386/Packag](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/binary-i386/Packag) es.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/dapper-backports/mai](http://old-releases.ubuntu.com/ubuntu/dists/dapper-backports/mai) n/debian-installer/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in '
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/P](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/P) ackages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-) i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Source](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Source) s.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/) Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i3](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i3) 86/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-) i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/So](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/So) urces.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/) Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/sourc](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/sourc) e/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/kde-353/dists/dapper/main/binary-i38](http://kubuntu.org/packages/kde-353/dists/dapper/main/binary-i38) 6/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://kubuntu.org/packages/koffice-151/dists/dapper/main/binary](http://kubuntu.org/packages/koffice-151/dists/dapper/main/binary) -i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/main/source/Sou](http://wine.budgetdedicated.com/apt/dists/dapper/main/source/Sou) rces.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free) /binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/sou](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/sou) rce/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free) /source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.czessi.net/ubuntu/dists/dapper/restricted/binary-](http://archive.czessi.net/ubuntu/dists/dapper/restricted/binary-) i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.czessi.net/ubuntu/dists/dapper/universe/binary-i3](http://archive.czessi.net/ubuntu/dists/dapper/universe/binary-i3) 86/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.czessi.net/ubuntu/dists/dapper/multiverse/binary-](http://archive.czessi.net/ubuntu/dists/dapper/multiverse/binary-) i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.czessi.net/ubuntu/dists/dapper/preview/binary-i38](http://archive.czessi.net/ubuntu/dists/dapper/preview/binary-i38) 6/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.czessi.net/ubuntu/dists/dapper/main/source/Source](http://archive.czessi.net/ubuntu/dists/dapper/main/source/Source) s.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.czessi.net/ubuntu/dists/dapper/restricted/source/](http://archive.czessi.net/ubuntu/dists/dapper/restricted/source/) Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.czessi.net/ubuntu/dists/dapper/universe/source/So](http://archive.czessi.net/ubuntu/dists/dapper/universe/source/So) urces.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.czessi.net/ubuntu/dists/dapper/multiverse/source/](http://archive.czessi.net/ubuntu/dists/dapper/multiverse/source/) Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.czessi.net/ubuntu/dists/dapper/preview/source/Sou](http://archive.czessi.net/ubuntu/dists/dapper/preview/source/Sou) rces.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/dists](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/dists) /breezy/non-free/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/dists](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/dists) /breezy/free/source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/dists](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/dists) /breezy/non-free/source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://www.mpe.mpg.de/~ach/kubuntu/dapper/./Sources.gz](http://www.mpe.mpg.de/~ach/kubuntu/dapper/./Sources.gz)  Could no t resolve 'netmon.iitb.ac.in'
Failed to fetch [http://apt.ubuntu.org.tw/ubtw/Packages.gz](http://apt.ubuntu.org.tw/ubtw/Packages.gz)  Could not resolve 'ne tmon.iitb.ac.in'
Failed to fetch [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-de](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-de) sktop/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-in](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-in) tern/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-nf](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-nf) sv4/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-vs](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-vs) erver/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-te](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-te) sting/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu/so](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu/so) urce/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-de](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-de) sktop/source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-in](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-in) tern/source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-nf](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-nf) sv4/source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-vs](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-vs) erver/source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://xgl.compiz.info/dists/dapper/main/source/Sources.gz](http://xgl.compiz.info/dists/dapper/main/source/Sources.gz)  Coul d not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://vdlinux.sourceforge.jp/dists/experimental/audacious/sourc](http://vdlinux.sourceforge.jp/dists/experimental/audacious/sourc) e/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.geole.de/dists/dapper/multiverse/binary-i386/Packa](http://ubuntu.geole.de/dists/dapper/multiverse/binary-i386/Packa) ges.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/breezy/main/binar](http://asher256-repository.tuxfamily.org/dists/breezy/main/binar) y-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/breezy/dupdate/bi](http://asher256-repository.tuxfamily.org/dists/breezy/dupdate/bi) nary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/breezy/french/bin](http://asher256-repository.tuxfamily.org/dists/breezy/french/bin) ary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://gauvain.tuxfamily.org/repos/dists/dapper/contrib/source/S](http://gauvain.tuxfamily.org/repos/dists/dapper/contrib/source/S) ources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://snapshots.gnomemeeting.net/ubuntu/dists/dapper/main/sourc](http://snapshots.gnomemeeting.net/ubuntu/dists/dapper/main/sourc) e/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://snapshots.voxgratia.org/ubuntu/dists/dapper/main/source/S](http://snapshots.voxgratia.org/ubuntu/dists/dapper/main/source/S) ources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/./Pac](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/./Pac) kages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://home.eng.iastate.edu/~superm1/dists/dapper/main/source/So](http://home.eng.iastate.edu/~superm1/dists/dapper/main/source/So) urces.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.cafuego.net/dists/dapper-cafuego/bcm43xx/binary-i3](http://ubuntu.cafuego.net/dists/dapper-cafuego/bcm43xx/binary-i3) 86/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.cafuego.net/dists/dapper-cafuego/all/source/Source](http://ubuntu.cafuego.net/dists/dapper-cafuego/all/source/Source) s.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.cafuego.net/dists/dapper-cafuego/bcm43xx/source/So](http://ubuntu.cafuego.net/dists/dapper-cafuego/bcm43xx/source/So) urces.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://repository.debuntu.org/dists/dapper/multiverse/source/Sou](http://repository.debuntu.org/dists/dapper/multiverse/source/Sou) rces.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://files.beep-media-player.org/packages/ubuntu/dists/dapper/](http://files.beep-media-player.org/packages/ubuntu/dists/dapper/) universe/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://files.beep-media-player.org/packages/ubuntu/dists/dapper/](http://files.beep-media-player.org/packages/ubuntu/dists/dapper/) main/source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://files.beep-media-player.org/packages/ubuntu/dists/dapper/](http://files.beep-media-player.org/packages/ubuntu/dists/dapper/) universe/source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/dapper-backports/mai](http://old-releases.ubuntu.com/ubuntu/dists/dapper-backports/mai) n/debian-installer/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in '
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/dapper-backports/mai](http://old-releases.ubuntu.com/ubuntu/dists/dapper-backports/mai) n/debian-installer/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in '
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/dapper-backports/mai](http://old-releases.ubuntu.com/ubuntu/dists/dapper-backports/mai) n/debian-installer/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in '
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binar](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binar) y-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted) /binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/sourc](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/sourc) e/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted) /source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/b](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/b) inary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse) /binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/s](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/s) ource/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse) /source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/bin](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/bin) ary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restrict](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restrict) ed/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://apt.ubuntu.org.tw/ubtw-testing/Packages.gz](http://apt.ubuntu.org.tw/ubtw-testing/Packages.gz)  Could not res olve 'netmon.iitb.ac.in'
Failed to fetch [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-te](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/dists/dapper/uniklu-te) sting/source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/ubuntu/main/binar](http://asher256-repository.tuxfamily.org/dists/ubuntu/main/binar) y-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/ubuntu/dupdate/bi](http://asher256-repository.tuxfamily.org/dists/ubuntu/dupdate/bi) nary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/ubuntu/french/bin](http://asher256-repository.tuxfamily.org/dists/ubuntu/french/bin) ary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/). /Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe) /binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiver](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiver) se/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/sou](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/sou) rce/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restrict](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restrict) ed/source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe) /source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiver](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiver) se/source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/deb](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/deb) ian-installer/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/bin](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/bin) ary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restrict](http://security.ubuntu.com/ubuntu/dists/dapper-security/restrict) ed/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/sou](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/sou) rce/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restrict](http://security.ubuntu.com/ubuntu/dists/dapper-security/restrict) ed/source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe) /binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiver](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiver) se/binary-i386/Packages.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe) /source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiver](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiver) se/source/Sources.gz  Could not resolve 'netmon.iitb.ac.in'
E: Some index files failed to download, they have been ignored, or old ones used  instead.
"
------------------------------------------------------------------------------------------------------------------------------
please help.... either give me a fix or if possible please give me a COMPLETE SOURCE LIST FOR DAPPER so that I can just replace my SOURCE LIST by that as I am a beginner in Linx...:(

---

