---
title: "php and sqlite"
date: 2005-05-17
forum: Server Platforms
---

### Post by sunset_studies on 2005-05-17
Hello,

Ubuntu has been great for me as a server so far, but I'm having trouble with the PHP Sqlite package. I installed *php4-sqlite* and restarted Apache but it doesn't work. A phpinfo() mentions nothing of sqlite, and any scripts attempting to use the sqlite functions show the typical error messages that you see when the PHP extenstion isn't installed. Googled for a solution, but so far I've had no luck...

Thanks

Edit:

I'm using Apache 2.

I came across this at [http://dev.riseup.net/bamboo/installation/](http://dev.riseup.net/bamboo/installation/) but can't find any other reference to the bug they mention:

[I]
 NOTE: there is a bug in the php4-sqlite which requires us to use the command line version for certain sqlite calls. In php5, this bug is fixed and we will not need the command line sqlite utils (package sqlite).[/I]

---

### Post by LordHunter317 on 2005-05-17
Make sure "extension=sqlite.so" is in your /etc/php4/apache2/php4.ini file and uncommented.  If it's not, add it and restart apache.

---

### Post by sunset_studies on 2005-05-18
Thanks for the reply,

I don't have an */etc/php4/apache2/php4.ini* but I do have an * /etc/php4/apache2/php.ini* . 

I tried the whole *extension=sqlite.so* thing before... and it didn't work. Funnily enough though, it works now  :)  I had definitely restarted Apache after making the change as well. I did make some other changes but I thought I had reversed them all before shutting down last night. Oh well, it all works now, thanks again.

---

### Post by gsuveg on 2005-07-21
im enabled the sqlite in php.ini, in phpinfo() im see the sqlite:

PHP Version 4.3.10-10ubuntu4
[..]
sqlite
SQLite support	enabled
PECL Module version 	1.0 $Id: sqlite.c,v 1.62.2.16 2004/01/17 00:29:37 edink Exp $
SQLite Library 	2.8.15
SQLite Encoding 	UTF-8

but with livedocs i have an error:

Fatal error: Call to undefined function: sqlite_exec() in ...php/livedocs/search.php on line 33

any idea ?

p.s.

#dpkg -l | grep sqli
ii  libsqlite0     2.8.15-3       SQLite shared library
ii  libsqlite3-0   3.0.8-3        SQLite 3 shared library
ii  php4-sqlite    1.0.2-5        PHP4 bindings to SQLite, a file-based SQL en
ii  python-sqlite  1.0.1-1ubuntu1 Python interface to SQLite
ii  python2.4-sqli 1.0.1-1ubuntu1 Python interface to SQLite
ii  sqlite         2.8.15-3       A command line interface for SQLite

---

