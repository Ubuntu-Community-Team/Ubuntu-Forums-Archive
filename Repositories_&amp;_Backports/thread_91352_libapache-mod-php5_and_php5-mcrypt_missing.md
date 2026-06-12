---
title: "libapache-mod-php5 and php5-mcrypt missing?"
date: 2005-11-17
forum: Repositories &amp; Backports
---

### Post by aouie on 2005-11-17
The libapache-mod-php5 and php5-mcrypt packages are not in the usual breezy repositories. I am trying to get php5 and Apache 1.3 setup at my personal computer to develop for a website that will have the same setup (the webhost will not support apache 2 as yet (supposedly cpanel doesn't support it as yet)).
  libapache2-mod-php5 description states "To use php5 with Apache 1.3, you probably want libapache-mod-php5 instead". This makes me wonder if the missing packages were an oversight or were they buggy or ...?
  I am hoping someone can point me to a repository that will include those modules (without breaking my breezy Kubuntu (Ubuntu with kubuntu-desktop)).
Sincerely,
Aouie

---

### Post by aouie on 2005-12-21
I found a package that was useful at < [http://www.apt-get.org/](http://www.apt-get.org/) >.
I selected just the following repository "http://packages.dotdeb.org/ stable all" binary and sources and installed php5, php5-common, php5-curl, php5-gd, php5-mash,  php5-mysql, php5-pgsql, php5-imap, php5-mcrypt and libapache-mod-php5. After installing this you can deselect this repository and reselect all the others. Just remember that the next time you mark all upgrades it will try to upgrade php5 to breezy's versions which may not be compatible with php-mcrypt from < [http://dotdeb.com/](http://dotdeb.com/) >.
The above is based partly on vague recollections from about a month ago, so proceed cautiously as I may not be able to assist with any hitches.
Sincerely,
Aouie

---

