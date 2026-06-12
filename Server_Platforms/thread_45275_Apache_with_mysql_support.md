---
title: "Apache with mysql support"
date: 2005-06-29
forum: Server Platforms
---

### Post by casualtie on 2005-06-29
I've got some issues get my webserver working optimal.
I've installed apache / php4 and mysql with synaptic.
But when I try to connect to a mysql database with a php file I get this error:
```

Fatal error: Call to undefined function: mysql_connect() in var/www/test/db_connect.php on line 2
```
Anyone know what I should do?

---

### Post by LordHunter317 on 2005-06-29
This has come up several times in the forum, please try searching first, next time.

Did you install php4-mysql?  If so, then make sure /etc/php4/apache2/php.ini has "extension=mysql.so" uncommented, then restart Apache.  Replace the path above as appropriate for Apache 1.3, if that is what you're running.

---

