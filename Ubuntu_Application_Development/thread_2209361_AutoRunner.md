---
title: "AutoRunner"
date: 2014-03-05
forum: Ubuntu Application Development
---

### Post by pixel2 on 2014-03-05
Hey, 

as Im advanced user of Linux-based systems, and Im very demanding user, I have started project called AutoRunner which (or will be as its development is underway but first scripts are finished now - once finished it will be publicly available on GitHub), simply assist bootloader (grub, lilo, etc) and adds usage of things like ports/interfaces so BL can take full advantage of each system installed. 

It will be done via core-unit so we had to install core-utility and prepare handler for extracting sub-module {*BOOT} from core module. Once extracted, we made a hard-punch shell script with handling assemblies, and sym-linked it to *BOOT/*F_LOADER value.

Developement is underway, and as such, is going pretty smoothly, with minor issues. We will update you on our progress.

First issue was (yes, its over now) Unity which isnt allowing core access (even to root). Just uninstall it (apt-get purge unity) and you are done. 
Later on our way: PHP inquist (hppa.exe would dump /sockets port). Removed ./sda1 and /sda2 then remounted them)
And many other issues.....see bugzilla

---

