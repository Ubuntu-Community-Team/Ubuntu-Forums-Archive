---
title: "Request: Drivel 2"
date: 2005-06-12
forum: Repositories &amp; Backports
---

### Post by bored2k on 2005-06-12
[http://www.dropline.net/drivel/screenshots.php](http://www.dropline.net/drivel/screenshots.php)
Hoary currently has version 1.2.3-2ubuntu2. Version 2 is hot.

---

### Post by angrykeyboarder on 2005-06-12
I second that request....

---

### Post by pampa on 2005-06-13
There is already a package for Hoary and it is maintained by the MOTU team.

[https://www.ubuntulinux.org/wiki/MOTUNewPackages](https://www.ubuntulinux.org/wiki/MOTUNewPackages)

---

### Post by bored2k on 2005-06-13
[QUOTE=pampa]There is already a package for Hoary and it is maintained by the MOTU team.

[https://www.ubuntulinux.org/wiki/MOTUNewPackages](https://www.ubuntulinux.org/wiki/MOTUNewPackages)[/QUOTE]
 I get dependency problems with. I still want the backport :D

---

### Post by vassie on 2005-06-13
*EDIT Ah you already tried that one :S

Ben

---

### Post by willrea on 2005-06-15
I almost got a working deb for it. I get this when I try to install it:

dpkg: error processing /media/hda4/drivel-2.0.0_2.0.0-1_i386.deb (--install):
 trying to overwrite `/usr/share/applications/mimeinfo.cache', which is also in package capplets-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)

---

### Post by angrykeyboarder on 2005-06-15
[QUOTE=pampa]There is already a package for Hoary and it is maintained by the MOTU team.

[https://www.ubuntulinux.org/wiki/MOTUNewPackages]("https://www.ubuntulinux.org/wiki/MOTUNewPackages")[/QUOTE]

That worked for me, but I'd still like to see it in a repository...

---

### Post by vassie on 2005-06-30
Where did it go? It's not on the MOTU page any more
Ben

---

### Post by angrykeyboarder on 2005-07-01
[QUOTE=vassie]Where did it go? It's not on the MOTU page any more
Ben[/QUOTE]

It's now in Breezy (Universe)

[http://packages.ubuntu.com/breezy/net/drivel](http://packages.ubuntu.com/breezy/net/drivel)

---

### Post by vassie on 2005-07-02
[QUOTE=angrykeyboarder]It's now in Breezy (Universe)

[http://packages.ubuntu.com/breezy/net/drivel](http://packages.ubuntu.com/breezy/net/drivel)[/QUOTE]
 What about for Hoary?

Ben

---

### Post by angrykeyboarder on 2005-07-02
[QUOTE=vassie]What about for Hoary?

Ben[/QUOTE]

You need to request it from backports.......

[http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)

---

### Post by Elmo on 2005-07-06
Alternatively you download the pre-compiled package for Fedora Core 3 from the drivel homepage ([http://www.dropline.net/drivel/download.php](http://www.dropline.net/drivel/download.php)) and then convert the package using alien ... seems to work for me in Hoary

---

### Post by vassie on 2005-07-06
I just found this one, and it works fine

[http://bolgo.cent.uji.es/ubuntu-dev/drivel/drivel_2.0.1-1_i386.deb](http://bolgo.cent.uji.es/ubuntu-dev/drivel/drivel_2.0.1-1_i386.deb)

Ben :)

---

### Post by filemanager on 2005-07-07
I run amd64, and I got my .deb package from here:

[http://ftp.psn.ru/debian-amd64/pool/main/d/drivel/](http://ftp.psn.ru/debian-amd64/pool/main/d/drivel/)

And it works fine! :)

EDIT: Just to specify, I downloaded version 2.0.1

EDIT: Actually, Drivel itself works fine, but when I open Synaptic it says the package is "broken"? shrug

---

### Post by filemanager on 2005-07-07
[QUOTE=Elmo]Alternatively you download the pre-compiled package for Fedora Core 3 from the drivel homepage ([http://www.dropline.net/drivel/download.php](http://www.dropline.net/drivel/download.php)) and then convert the package using alien ... seems to work for me in Hoary[/QUOTE]
 Do you use i386 or amd64?

---

### Post by filemanager on 2005-07-07
[QUOTE=filemanager]Do you use i386 or amd64?[/QUOTE]
 I uninstalled it because I don't like when things are "broken", even though it was working fine, , then I did a search for "drivel" in synaptic, and it found v1.2.3, so I installed that, and now it works and no "broken" packages! Yay!!

---

