---
title: "How to create a deb package?"
date: 2005-06-06
forum: The Cafe
---

### Post by dierre on 2005-06-06
Hello!

I'm playing around with my ubuntu... I've written some shell scripts in order to automate some works I have to do; in order to install them on multiple machines I would like to create a package so that I can use apt / dbpkg.

I've never created a .deb, so here is something new for me to learn. :-)
Googling around I found that on debian systems there should be the /usr/share/doc/HOWTO/Debian-Binary-Packaging-HOWTO explaining how to do it. What is the analogue ubuntu howto called? What package provides it?

Thank you!

---

### Post by XDevHald on 2005-06-06
I found a link that might be of some good use to you on how to do this.

[http://linuxdevices.com/articles/AT8047723203.html](http://linuxdevices.com/articles/AT8047723203.html)

---

### Post by az on 2005-06-06
You want the new maintainers guide:

[http://www.debian.org/doc/manuals/maint-guide/](http://www.debian.org/doc/manuals/maint-guide/)

Also , from the wiki:
[http://www.ubuntulinux.org/wiki/PackageMaintenanceWorkshop](http://www.ubuntulinux.org/wiki/PackageMaintenanceWorkshop)
[http://www.ubuntulinux.org/wiki/HowToBuildDebianPackagesFromScratch](http://www.ubuntulinux.org/wiki/HowToBuildDebianPackagesFromScratch)

and of course:
[http://women.alioth.debian.org/wiki/index.php/English/BuildingWithoutHelper](http://women.alioth.debian.org/wiki/index.php/English/BuildingWithoutHelper)

---

### Post by oddabe19 on 2005-06-06
[QUOTE=azz]You want the new maintainers guide:

[http://www.debian.org/doc/manuals/maint-guide/](http://www.debian.org/doc/manuals/maint-guide/)

Also , from the wiki:
[http://www.ubuntulinux.org/wiki/PackageMaintenanceWorkshop](http://www.ubuntulinux.org/wiki/PackageMaintenanceWorkshop)
[http://www.ubuntulinux.org/wiki/HowToBuildDebianPackagesFromScratch](http://www.ubuntulinux.org/wiki/HowToBuildDebianPackagesFromScratch)

and of course:
[http://women.alioth.debian.org/wiki/index.php/English/BuildingWithoutHelper](http://women.alioth.debian.org/wiki/index.php/English/BuildingWithoutHelper)[/QUOTE]
 I personally use Checkinstall
the how-to i wrote is here, it's really easy to use.
[http://www.ubuntuforums.org/showthread.php?t=2356](http://www.ubuntuforums.org/showthread.php?t=2356)

I found making .deb packages by hand is a mess sometimes, so i just go towards that.

---

### Post by dierre on 2005-06-07
Thanks to everybody for their help!

---

### Post by az on 2005-06-07
[QUOTE=oddabe19]I personally use Checkinstall
the how-to i wrote is here, it's really easy to use.
[http://www.ubuntuforums.org/showthread.php?t=2356](http://www.ubuntuforums.org/showthread.php?t=2356)

I found making .deb packages by hand is a mess sometimes, so i just go towards that.[/QUOTE]

Checkinstall is to deb package what a half-eaten bag of potato chips is to a plate of sushi.

It serves a purpose but it is not a replacement.

---

