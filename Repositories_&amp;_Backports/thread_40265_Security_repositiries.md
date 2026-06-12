---
title: "Security repositiries"
date: 2005-06-08
forum: Repositories &amp; Backports
---

### Post by simber on 2005-06-08
Hello you all

I m new to ubuntu, not new to linux or debian

I m having trouble doing an apt-get update, this is my sources.list file

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

I m getting the following error :

apt-get update
Des:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Des:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Des:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Des:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Des:5 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16,9kB]
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Des:6 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages [25,4kB]
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Des:7 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources [6339B]
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Obj [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Obj [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Obj [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Obj [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Obj [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Obj [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Obj [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Obj [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Descargados 48,8kB en 3s (15,6kB/s)
Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz)  La suma MD5 difiere (MD5 sum difers)
Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz)  La suma MD5 difiere
Leyendo lista de paquetes... Hecho
W: No se puede leer la lista de paquetes fuente [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas
E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
root@subgerencia:/home/rsierra #

Thanks for your help

---

### Post by kokotero on 2005-06-14
same here

is this a configuration error or is there any error in some mirrors?

---

### Post by gmc on 2005-06-14
The US/CA servers are borked at the moment. I found changing us. to fr. worked for me.

G.

---

### Post by ubuntu_demon on 2005-06-14
please continue here :

[http://www.ubuntuforums.org/showthread.php?t=41647](http://www.ubuntuforums.org/showthread.php?t=41647)

---

