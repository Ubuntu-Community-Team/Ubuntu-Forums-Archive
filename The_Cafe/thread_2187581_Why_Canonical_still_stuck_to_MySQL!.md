---
title: "Why Canonical still stuck to MySQL?!"
date: 2013-11-12
forum: The Cafe
---

### Post by mbnoimi on 2013-11-12
Hi all,

I wonder why Canonical still stuck to MySQL while the other Linux gurus moved to MariaDB?!

MariaDB compatible with old (and current) MySQL versions so most apps which used MySQL will work fine with MariaDB

---

### Post by castrojo on 2013-11-12
Someone needed to package it for Debian/Ubuntu and it's taking time to do it right, see: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=565308](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=565308)

Discussion of what's going to happen happens at UDS next week if you want to participate: [http://summit.ubuntu.com/uds-1311/meeting/22109/servercloud-1311-mysql-alternatives/](http://summit.ubuntu.com/uds-1311/meeting/22109/servercloud-1311-mysql-alternatives/)

---

### Post by mbnoimi on 2013-11-12
```
 Discussion of what's going to happen happens at UDS next week if you want to participate: http://summit.ubuntu.com/uds-1311/me...-alternatives/ 
```
Oops it seems that MariaDB needs a long time to be available in Ubuntu repositories!!!
They suggests to keep MySQL in the main for 14.04 which means MariaDB will be available at least in 14.10... I think Fedora and OpenSuSE made it available since a year ago!

---

### Post by monkeybrain20122 on 2013-11-12
It is available through ppa.
[https://downloads.mariadb.org/mariadb/repositories/#mirror=weathercity&distro=Ubuntu&version=5.5&distro_release=saucy](https://downloads.mariadb.org/mariadb/repositories/#mirror=weathercity&distro=Ubuntu&version=5.5&distro_release=saucy)

---

