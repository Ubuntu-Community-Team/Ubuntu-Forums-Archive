---
title: "PECL Extentions"
date: 2006-07-21
forum: Server Platforms
---

### Post by alecjw on 2006-07-21
How do I install PECL extentions for PHP? I assume I need a compiler, but how do I install the compiler? Whenever i try to run aptitude install gcc or aptitude install make, it asks me to put the cd in /cdrom/ but I don't have /cdrom/ any more, it broke. Now, whenever I put a CD drive in, it calls it cdrom1, cdrom2 etc. Is there any way of installing it without a CD drive?

---

### Post by lisje on 2006-08-11
I hope you already found a solution but here it goes:

* if you don't want the cd to be called when you want to install something, remove the cdrom-line from your '/etc/apt/sources.list'

* for pecl ... I've installed php-pear and the php5-dev (basically the development files for the php you're using)

it should work :-)

greets,
Lisje


**edit**
also usefull: [http://be2.php.net/manual/en/install.pecl.php](http://be2.php.net/manual/en/install.pecl.php)

---

