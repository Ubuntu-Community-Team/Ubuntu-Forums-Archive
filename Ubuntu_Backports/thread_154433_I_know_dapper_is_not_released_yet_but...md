---
title: "I know dapper is not released yet but.."
date: 2006-04-03
forum: Ubuntu Backports
---

### Post by siimo on 2006-04-03
i wish they'd get the BackPorts rolling already ](*,) 

it's gonna be out of date if it stays frozen till 06/06/2006. 
<cough>gaim</cough>:???:

---

### Post by hw-tph on 2006-04-19
I suggest you build your own Gaim package and set up a repository for it. It's not that hard, and instead of complaining you would be doing the community a service.


Håkan

---

### Post by jdong on 2006-04-23
Sorry; can't really start backports for Dapper until Edgy starts. If you're really that bleeding edge, I highly recommend that you learn the process for building updated packages (it's quite simple, actually), so you can roll your own backports.

---

### Post by moberry on 2006-05-06
> If you're really that bleeding edge, I highly recommend...

Or, use debian sid (what ubuntu starts out at) I go back and forth between sid, and ubuntu (can't decided what i want)

---

### Post by MichaëlVD on 2006-05-08
You can also add this to your sources.list:

deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./
deb-src [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

This gave me newer versions of Gaim and Rhythmbox.

---

### Post by MaX on 2006-05-09
[QUOTE=jdong]Sorry; can't really start backports for Dapper until Edgy starts. If you're really that bleeding edge, I highly recommend that you learn the process for building updated packages (it's quite simple, actually), so you can roll your own backports.[/QUOTE]
Where do I look for instructions? (HOW-TO?)

---

### Post by hw-tph on 2006-05-10
You could start by reading the [Debian new maintainer's guide](http://www.debian.org/doc/manuals/maint-guide), it is the general authority getting started with Debian packaging.

I suggest you download and install it - the package is called maint-guide.  I also suggest you grab a few other documentation packages that may come in handy: debian-reference, debian-policy and developers-reference.


Håkan

---

### Post by ubuntu_demon on 2006-05-10
regarding packaging. I think this might be a good place to start. It's also available from the Dapper help system. I plan to follow this guide someday when I'm bored :

[http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html)

AFAIK there are no specific (ubuntu) backport howtos.

---

### Post by jdong on 2006-05-11
(1) apt-get source <packagename>

(2) Go into newly unpacked folder

(3) Edit debian/changelog. Add "~0custom1" to the version number in parentheses.

(4) Run [b]apt-get build-dep <packagename>

(5) Run dpkg-buildpackage -rfakeroot -b


You're done :)

---

### Post by ubuntu_demon on 2006-05-17
[QUOTE=jdong](1) apt-get source <packagename>

(2) Go into newly unpacked folder

(3) Edit debian/changelog. Add "~0custom1" to the version number in parentheses.

(4) Run [b]apt-get build-dep <packagename>

(5) Run dpkg-buildpackage -rfakeroot -b


You're done :)[/QUOTE]
thnx for the information :)

---

