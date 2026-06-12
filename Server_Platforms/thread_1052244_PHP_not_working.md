---
title: "PHP not working"
date: 2009-01-27
forum: Server Platforms
---

### Post by suniyo on 2009-01-27
I have installed apache2 with php5 and mysql. Now when I start all the servers everything goes well until I execute php scripts. PHP behaves strangely, I have checked that it is working and module for apache2 is also installed but it doesn't execute scripts with php. phpinfo says that everything is okey but it doesn't actually run scripts. Where is the problem? with apache or with php. httpd.conf is empty and apache2.conf is at default value I have not changed anything there. 

Problem is still there even after restarting apache and sql. 
Thanks in advance.

---

### Post by spiderbatdad on 2009-01-27
probably permissions error, ie. ownership of scripts.

---

### Post by suniyo on 2009-11-11
> **spiderbatdad said:**
> probably permissions error, ie. ownership of scripts.

It is due to this bug: [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/451314](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/451314) - [SRU] PHP 5.2.10 zlib bug remains for 32bit

---

### Post by suniyo on 2009-11-11
By the way it was solved with an upgrade

---

