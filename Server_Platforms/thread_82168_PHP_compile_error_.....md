---
title: "PHP compile error ...."
date: 2005-10-26
forum: Server Platforms
---

### Post by dbee on 2005-10-26
Anyone know why my php compile won't work ?

I've googled it but there doesn't seem to be an answered post ...

root@ubuntu:/usr/local/php # ./configure --with-mysql=/usr/local/mysql --with-apache=/usr/local/apache2/ --enable-safe-mode --with-apxs2=/usr/local/apache2/bin/apxs
--------
--------
configure: error: Invalid Apache directory - unable to find httpd.h under /usr/local/apache2/include/httpd.h

... all the files are in their proper place, and httpd.h is there.
It's just that the compile can't find it for some reason.

---

### Post by wellery on 2005-10-26
looks like apache isn't installed properly because it's missing httpd.h. Why are you tring to compile it. Have you tried installing it from the repositories? You can install both apache and php from the repositories.

---

