---
title: "lighttpd + fastcgi php + mysql"
date: 2006-09-01
forum: Server Platforms
---

### Post by trancephorm on 2006-09-01
I managed to setup lighttpd and php through fastcgi with no problems and very quickly, but i noticed php-cgi lacks support for mysql.... ok, so i added extension=mysql.so to /etc/php/cgi/php.ini  but there is still no mysql support in phpinfo.... 

someone's got a hint? :)

---

### Post by celloandy on 2006-09-01
Did you install the php5-mysql (or php4-mysql) package?  That should be all it takes, and that installation should automatically make the necessary changes to your php.ini files to enable mysql.

Andrew

---

### Post by trancephorm on 2006-09-01
I'm sure php4-mysql package is installed...

>>>dpkg -l | grep php4
ii  libapache2-mod-php4                4.4.2-1build1                server-side, HTML-embedded scripting languag
ii  php4                               4.4.2-1build1                server-side, HTML-embedded scripting languag
ii  php4-cgi                           4.4.2-1build1                server-side, HTML-embedded scripting languag
ii  php4-common                        4.4.2-1build1                Common files for packages built from the php
ii  php4-dev                           4.4.2-1build1                Files for PHP4 module development
ii  php4-mysql                         4.4.2-1build1                MySQL module for php4

---

