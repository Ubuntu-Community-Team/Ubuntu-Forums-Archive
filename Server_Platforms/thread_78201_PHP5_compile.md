---
title: "PHP5 compile"
date: 2005-10-18
forum: Server Platforms
---

### Post by dbee on 2005-10-18
I really don't know what I'm doing wrong here

root@ubuntu:/home/babo/Desktop/php-5.0.5 # ./configure --with-apache=/usr/local/apache2/include/ --with-mysql --enable-track-vars
................
checking for Apache 1.x module support via DSO through APXS... no
checking for Apache 1.x module support... no
configure: error: Invalid Apache directory - unable to find httpd.h under /usr/local/apache2/include/

root@ubuntu:/home/babo/Desktop/php-5.0.5 # ls /usr/local/apache2/include | grep httpd.h
httpd.h

I mean the file is right there, I'm compiling in root ... why doesnt' the configure see it ??

---

### Post by dbee on 2005-10-18
thought I had it their ,but no luck 

I used 

./configure --enable-so

and it tells me that mod_so is already compiled into httpd

then I remove --enable-so

and it tells me to make sure mod_so is compiled into httpd

---

### Post by dbee on 2005-10-18
oops

---

