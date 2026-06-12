---
title: "Help finding PHP5-MCRYPT"
date: 2005-11-04
forum: Server Platforms
---

### Post by FrostByghte on 2005-11-04
Hello,

Just installed a few ubuntu servers and I'm having a tough time locating php5-mcrypt.  Anyone know where I can find this for the amd64?  Thank you.

---

### Post by FrostByghte on 2005-11-07
Is this one of those lost cause questions? :)  New to ubuntu community, straight from Gentoo and interested in trying out a server but finding all the parts for php5 that I need is not going too well.  Running on amd64, woot! :)  Any help appreciated...or should I just stick with php4?  I really hate to use php4 since this would be an excellent time to go with php5.

---

### Post by ben72 on 2005-11-11
I'm not sure this helps, but you can find a php5-mcrypt package here..

[http://www1.apt-get.org/search.php?query=php&submit=&arch%5B%5D=i386](http://www1.apt-get.org/search.php?query=php&submit=&arch%5B%5D=i386)

But I got some strange dependancies so I gave it up. Please let me know if you get it to work.

---

### Post by aouie on 2005-12-21
I found a package that was useful at < [http://www.apt-get.org/](http://www.apt-get.org/) >.
I selected just the following repository "http://packages.dotdeb.org/ stable all" binary and sources and installed php5, php5-common, php5-curl, php5-gd, php5-mash,  php5-mysql, php5-pgsql, php5-imap, php5-mcrypt and libapache-mod-php5. After installing this you can deselect this repository and reselect all the others. Just remember that the next time you mark all upgrades it will try to upgrade php5 to breezy's versions which may not be compatible with php-mcrypt from < [http://dotdeb.com/](http://dotdeb.com/) >.
The above is based partly on vague recollections from about a month ago, so proceed cautiously as I may not be able to assist with any hitches.
Sincerely,
Aouie

---

