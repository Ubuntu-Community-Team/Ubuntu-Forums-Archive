---
title: "Archive problems.. server down?!"
date: 2006-08-01
forum: Repositories &amp; Backports
---

### Post by bmonkey on 2006-08-01
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper/universe ethereal 0.99.0-1ubuntu1
  Connection timed out
It has been like this for two days - anyone know whats wrong with it? Whenever i need a package from za.archive.ubuntu.com it times out..

anyone got any ideas or advice? it would be greatly appreciated

---

### Post by pomegranate on 2006-08-01
I'm also getting what appears to be the same problem, but as I'm a total Ubunutu (Linux for that matter) newcomer, I don't know for sure whether it's  a problem with the server, or my installation, or what... What I'm experiencing is that when I go to install new programs, the Downloading package information dialogue box appears and packages start downloading, but most fail. Is this likely the same problem?

---

### Post by bmonkey on 2006-08-01
yea thats what i get - im pretty sure its a server problem cos my install is not even 24 hours old and i havent messed with sources.list either.. 

Is your error for the za.archive.ubuntu.com aswell?

---

### Post by infoseeker on 2006-08-02
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be upgraded:
  dcoprss kdenetwork kdict kget knewsticker ksirc ktalkd kwifimanager librss1 lisa
10 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2569kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/universe librss1 4:3.5.2-0ubuntu6.2
  404 Not Found
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/universe dcoprss 4:3.5.2-0ubuntu6.2
  404 Not Found
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/universe kdict 4:3.5.2-0ubuntu6.2
  404 Not Found
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/universe kget 4:3.5.2-0ubuntu6.2
  404 Not Found
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/universe knewsticker 4:3.5.2-0ubuntu6.2
  404 Not Found
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/universe ksirc 4:3.5.2-0ubuntu6.2
  404 Not Found
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/universe kwifimanager 4:3.5.2-0ubuntu6.2
  404 Not Found
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/universe kdenetwork 4:3.5.2-0ubuntu6.2
  404 Not Found
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/universe lisa 4:3.5.2-0ubuntu6.2
  404 Not Found
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/universe ktalkd 4:3.5.2-0ubuntu6.2
  404 Not Found

---

### Post by Paul Bramscher on 2006-08-02
I've run "apt-get update" and I'm getting this here in the US:

Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be upgraded:
  eog file-roller gnome-accessibility-themes gnome-applets gnome-applets-data
  gnome-games gnome-games-data gnome-menus gnome-session gnome-themes
  gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast
  gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist
  gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth
  gtk2-engines-thinice language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base libeel2-2 libeel2-data
  libgnome-menu2 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libnautilus-burn3
  libtotem-plparser1 nautilus-cd-burner python-gmenu totem totem-gstreamer
  yelp
37 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1513kB/22.7MB of archives.
After unpacking 172kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-highcontrast 1 :2.7.4.is.2.6.10-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-thinice 1:2.7. 4.is.2.6.10-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-crux 1:2.7.4.i s.2.6.10-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-redmond95 1:2. 7.4.is.2.6.10-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-lighthouseblue  1:2.7.4.is.2.6.10-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-smooth 1:2.7.4 .is.2.6.10-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-mist 1:2.7.4.i s.2.6.10-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-clearlooks 1:2 .7.4.is.2.6.10-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-industrial 1:2 .7.4.is.2.6.10-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libtotem-plparser1 1.4.3-0u buntu1
  404 Not Found [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main totem-gstreamer 1.4.3-0ubun tu1
  404 Not Found [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main totem 1.4.3-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk) 2-engines-highcontrast_2.7.4.is.2.6.10-0ubuntu1_i386.deb  404 Not Found [IP: 146 .137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk) 2-engines-thinice_2.7.4.is.2.6.10-0ubuntu1_i386.deb  404 Not Found [IP: 146.137. 96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk) 2-engines-crux_2.7.4.is.2.6.10-0ubuntu1_i386.deb  404 Not Found [IP: 146.137.96. 7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk) 2-engines-redmond95_2.7.4.is.2.6.10-0ubuntu1_i386.deb  404 Not Found [IP: 146.13 7.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk) 2-engines-lighthouseblue_2.7.4.is.2.6.10-0ubuntu1_i386.deb  404 Not Found [IP: 1 46.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk) 2-engines-smooth_2.7.4.is.2.6.10-0ubuntu1_i386.deb  404 Not Found [IP: 146.137.9 6.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk) 2-engines-mist_2.7.4.is.2.6.10-0ubuntu1_i386.deb  404 Not Found [IP: 146.137.96. 7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk) 2-engines-clearlooks_2.7.4.is.2.6.10-0ubuntu1_i386.deb  404 Not Found [IP: 146.1 37.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk) 2-engines-industrial_2.7.4.is.2.6.10-0ubuntu1_i386.deb  404 Not Found [IP: 146.1 37.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-p](http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-p) lparser1_1.4.3-0ubuntu1_i386.deb  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstr](http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstr) eamer_1.4.3-0ubuntu1_i386.deb  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_1.4](http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_1.4). 3-0ubuntu1_all.deb  404 Not Found [IP: 146.137.96.7 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-mis sing?

---

### Post by sbaker33 on 2006-08-02
So this would be an issue with the servers or repositories?  I have three packages that I can not update on a brand new installation.  If it is a server/repo issue I'll just wait to see when it is fixed otherwise I'll reinstall.

---

### Post by Silver Surfer on 2006-08-02
It can't be your new install, I am getting the same errors, and this machine has been up and running since warty.

---

### Post by infoseeker on 2006-08-02
Maybe its got something to do with the release of KDE 3.5.4 ?

[http://www.kde.org/announcements/announce-3.5.4.php](http://www.kde.org/announcements/announce-3.5.4.php)

---

### Post by bigbird_594 on 2006-08-02
Am having the same problem: 

> Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser1_1.4.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser1_1.4.3-0ubuntu1_i386.deb)
  404 Not Found [IP: 146.137.96.7 80]

---

### Post by bmonkey on 2006-08-02
it could be the new release of the kde but i doubt that cos if the servers were overloaded you should be able to get them sometime.. but you cant get em anytime.. :/ altho i managed to get 14 of my 15 updates about 4 hours ago so i think they must be fixing something

---

### Post by bigbird_594 on 2006-08-02
Am having the same problem: 

> Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser1_1.4.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser1_1.4.3-0ubuntu1_i386.deb)
  404 Not Found [IP: 146.137.96.7 80]

---

### Post by bmonkey on 2006-08-02
So what i found out it is , is that the file doesnt actually exist on the server - which means they are in the process of adding them i hope. :/ what i dont understand is that they give you dead links - why not make sure the files are on the server BEFORE giving out the update notices :(

what i did now was just downloading my deb package from another repository
[http://us.archive.ubuntu.com/ubuntu/pool/main/z/zenity/zenity_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/z/zenity/zenity_2.14.3-0ubuntu1_i386.deb) rather than the link given to me
[http://**za](http://**za)**.archive.ubuntu.com/ubuntu/pool/main/z/zenity/zenity_2.14.3-0ubuntu1_i386.deb

---

### Post by coltey on 2006-08-02
I'm new to ubuntu and I have install v6.06 Dapper and I am having trouble with the archive server as well. I am receiveing the following when I try to update through add/remove with the following:
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) The HTTP server sent an invalid reply header [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]

Is someone working on the server or what, I have been trying this update for the last three days and receive the same errors each day. Will try again tomorrow and see what happens.

---

### Post by sbaker33 on 2006-08-02
My issues seem to have been resolved.  I was able to upgrade all the packages this time around.

---

### Post by McDuff on 2006-08-03
i'm having the same problem with the austrian servers.
yesterday i resolved it by using the us-servers, but today neither works. i'm getting the following error:
```
Konnte http://at.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb nicht holen  404 Not Found
Konnte http://at.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector_0.1.20.1_all.deb nicht holen  404 Not Found
Konnte http://at.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-common_0.1.20.1_all.deb nicht holen  404 Not Found
```

---

### Post by sbaker33 on 2006-08-03
OK, It was better.  I am having the same problem with the same server/repository again today...

---

### Post by greenstar on 2006-08-03
Look at the following threads & see if it helps.

[http://www.ubuntuforums.org/showthread.php?t=221215](http://www.ubuntuforums.org/showthread.php?t=221215), especially [my post]("http://www.ubuntuforums.org/showpost.php?p=1290201&postcount=9").

[http://www.ubuntuforums.org/showthread.php?t=220988](http://www.ubuntuforums.org/showthread.php?t=220988)

Greenstar

---

### Post by spin2cool on 2006-08-03
ditto.

Could not connect to archive.ubuntu.com:80 (82.211.81.182)

---

