---
title: "wine support for boson software"
date: 2009-05-01
forum: Wine
---

### Post by hhlp on 2009-05-01
when wine will support boson product netsim and exim i don't wnat to use a virtual machine only for this stuff if anyone can help:

Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty


Linux 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009

wine:
  Instalados: 1.1.20~winehq0~ubuntu~9.04-0ubuntu3
  Candidato: 1.1.20~winehq0~ubuntu~9.04-0ubuntu3
  Tabla de versión:
 *** 1.1.20~winehq0~ubuntu~9.04-0ubuntu3 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
        100 /var/lib/dpkg/status
     1.0.1-0ubuntu6 0
        500 [http://mirror.cpsc.ucalgary.ca](http://mirror.cpsc.ucalgary.ca) jaunty/universe Packages

i can't install netframework show an error and don't configure y also install with winetrick but boson show and error.

---

### Post by NightMKoder on 2009-05-01
dotnet framework doesn't run well under wine. You can install 2.0 by using winetricks, but its known to not run very reliably. 3.0 does not even install yet.

---

### Post by asdfoo on 2009-05-01
remove your wineprefix and use winetricks to install dotnet20 before running the installer

mv ~/.wine ~/.wine-bad
wget kegel.com/wine/winetricks
sh winetricks dotnet20

---

### Post by hhlp on 2009-05-02
i instaled frmework 2.0 but the problem is what boson exim try to install netframework 1.1 sp1 and never finish configuring is a loop trying to configure :

i also try to install donet11 finish well, i also try to download sp1 directly but i get and error :

this is the error :

file attach error nro. 1

and i also attach and image.

if you try to install both donet 2.0 first and donet1.1 later this fail :

this is the error

file attach error nro. 2

regards.,[ATTACH][ATTACH]112176[/ATTACH]

[ATTACH]112178[/ATTACH][/ATTACH]

---

