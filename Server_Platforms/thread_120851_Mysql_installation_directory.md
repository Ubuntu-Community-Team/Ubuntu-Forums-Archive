---
title: "Mysql installation directory?"
date: 2006-01-23
forum: Server Platforms
---

### Post by Vegettex on 2006-01-23
Heya all,

I just did sudo apt-get install mysql-server. to install a mysql server on my pc, but where does it get installed? I need to know because then i can configure that with my webmin. By default it should be in /usr/local/mysql but there ain't no such directory there.

Anybody knows?

Thanks in advance!

---

### Post by spectre_25gt on 2006-01-23
```
which mysql
``` will tell you where the mysql connector executable is as long as it's in your path. On my install mysql is /usr/bin/mysql, mysqld is /usr/sbin/mysqld and config is in /etc/mysql/.

---

### Post by Vegettex on 2006-01-24
Thanks that did the trick :) Learned another new command :)

---

