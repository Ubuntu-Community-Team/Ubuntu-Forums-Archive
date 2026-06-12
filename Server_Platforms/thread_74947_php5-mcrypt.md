---
title: "php5-mcrypt"
date: 2005-10-13
forum: Server Platforms
---

### Post by punkass on 2005-10-13
Hi all,

Was just curious if any one knew why there is no php5-mcrypt module.

I noticed there was a php4 one....just no php5


thanks.

---

### Post by ben72 on 2005-10-15
I'm also wondering why there is no php5-mcrypt and php5-pear packages. Those are needed for installing vhcs on breezy.

---

### Post by aouie on 2005-12-21
I found a package that was useful at < [http://www.apt-get.org/](http://www.apt-get.org/) >.
I selected just the following repository "http://packages.dotdeb.org/ stable all" binary and sources and installed php5, php5-common, php5-curl, php5-gd, php5-mash,  php5-mysql, php5-pgsql, php5-imap, php5-mcrypt and libapache-mod-php5. After installing this you can deselect this repository and reselect all the others. Just remember that the next time you mark all upgrades it will try to upgrade php5 to breezy's versions which may not be compatible with php-mcrypt from < [http://dotdeb.com/](http://dotdeb.com/) >.
The above is based partly on vague recollections from about a month ago, so proceed cautiously as I may not be able to assist with any hitches.
Sincerely,
Aouie

---

