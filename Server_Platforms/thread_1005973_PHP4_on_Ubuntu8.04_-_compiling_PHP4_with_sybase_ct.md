---
title: "PHP4 on Ubuntu8.04 - compiling PHP4 with sybase_ct errors"
date: 2008-12-08
forum: Server Platforms
---

### Post by djhmateer on 2008-12-08
Hi

For legacy reasons I need to run PHP4.  Am building an Ubuntu8.04
server with Apache2 prefork.  I've compiled PHP from source and got it
working.

However I need to use the sybase_ct library, but can't get it to
compile.

So have been compiling with:

 ./configure --prefix=/usr/share/php --with-apxs2=/usr/bin/apxs2 --
with-config-file-path=/etc/apache2/php --with-sybase-ct

 ./configure --prefix=/usr/share/php --with-apxs2=/usr/bin/apxs2 --
with-config-file-path=/etc/apache2/php --with-sybase-ct=shared

 ./configure --prefix=/usr/share/php --with-apxs2=/usr/bin/apxs2 --
with-config-file-path=/etc/apache2/php --with-sybase-ct=/usr/src/
php-4.4.9/ext

Am always getting config errors of

configure: error: ctpublic.h missing!

even though I put it in /usr/src/php4.4.9/ext.. tried putting it in /
oct/sybase

Any ideas?

Regards

---

### Post by djhmateer on 2008-12-09
[http://ubuntuforums.org/showthread.php?t=796515&highlight=php4](http://ubuntuforums.org/showthread.php?t=796515&highlight=php4)

---

