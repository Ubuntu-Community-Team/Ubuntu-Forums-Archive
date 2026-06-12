---
title: "openssl.so not found, php5"
date: 2007-07-17
forum: Server Platforms
---

### Post by Iradiatul on 2007-07-17
Hi!

I am trying to put the openssl extension in php5.
I have ubuntu installed on my machine.

I have the sources from php and i runned:

'./configure' '--enable-versioning' '--with-layout=GNU' '--with-config-file-scan-dir=/etc/php5/apache2' '--disable-all' '--enable-libxml' '--with-libxml-dir=/usr/include' '--enable-reflection' '--program-prefix=' '--disable-cgi' '--with-regex=php' '--with-zend-vm=CALL' '--disable-ipv6' '--prefix=/usr/lib' '--with-openssl'

then

make

and

make install

As a result in /var/log/apache2/error.log :

PHP Warning:  PHP Startup: Invalid library (maybe not a PHP library) 'libssl.so'  in Unknown on line 0
[Tue Jul 17 13:11:29 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 mod_ssl/2.0.55 OpenSSL/0.9.8b mod_perl/2.0.2 Perl/v5.8.8 configured -- resuming normal operations
unable to write 'random state'
unable to write 'random state'
...

Running 
locate openssl.so (also with updatedb before) i cannot find the file


Please help a newbie,

Any hint or indication would be greatly appreciated.

Thank you

---

### Post by Iradiatul on 2007-07-18
FIXED!


SSLOptions +StdEnvVars


was missing!

---

