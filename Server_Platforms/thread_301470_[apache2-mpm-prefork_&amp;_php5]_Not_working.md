---
title: "[apache2-mpm-prefork &amp; php5] Not working"
date: 2006-11-17
forum: Server Platforms
---

### Post by cataenry on 2006-11-17
Hi all,
i need to set up an offline apache2+php5 server.
I've installed apache2-mpm-prefork and libapache-mod-php5,
then a2enmod php5 and all went fine.
Cgi scripts (like gitweb.cgi for example) are working,
while with any kind of php file i've a 500 internal server error.
Shouldn't be a file permission issue, since i've read about how dir and file should be setted up: dir 711|755 file 700|711|755 and they are fine.

Any hint?
Thanks for the attention! :)

cataenry

---

### Post by cataenry on 2006-11-17
Solved, my mistake,
you can remove this msg! :)
Bye

---

