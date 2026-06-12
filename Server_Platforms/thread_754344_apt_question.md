---
title: "apt question"
date: 2008-04-13
forum: Server Platforms
---

### Post by mattack on 2008-04-13
How do you install a package with alternate dependencies? For instance, I want to install MediaWiki but don't want to use the default MySQL database as I already have PostgreSQL installed and running. If you ```
# aptitude show mediwiki1.10
Package: mediawiki1.10
State: not installed
Version: 1.10.2-1
Priority: optional
Section: universe/web
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 17.3M
Depends: apache2 | httpd, php5, **php5-mysql | php5-pgsql**, php5-cli, mime-support, debconf (>= 0.5) | debconf-2.0
Recommends: **mysql-server | postgresql-8.1**
```
How do I get it installed with postgresql support instead of mysql?

---

### Post by koenn on 2008-04-13
install the dependencies   (php5-pgsql, postgresql-8.1)  first.
then, when you install mediawiki, it will notice that its dependencies are satisfied, and continues to install without any trouble.

If I remember correctly, mediawiki's install instructions also recommend to have apache and php installed beforehand.
part of the initial configuration of mediawiki is done through its web interface and that won't work without those.

---

### Post by mattack on 2008-04-14
Duh...  why didn't I think of that?
Turns out that wasn't quite enough though... Even after installing php5-pgsql, aptitude tried to install mysql-server. WTF?
So ```
sudo aptitude install -R mediawiki
``` takes care of that by telling it to not install recommended packages.

---

### Post by koenn on 2008-04-14
strange. I overlooked the recommends and forgot to take into account that aptitude treats reccommends as real dependencies. 

Still, if aptitude thinks it needs to install mysql, that possible means that your postgresql isn't the correct version, or wasn't installed in a way that apt would know about it (i.e. from a .deb package, through apt, aptitude or synaptic, or another program that uses one of those as its backend), or that you have deleted apt's logs about installed packages or something like that.

---

