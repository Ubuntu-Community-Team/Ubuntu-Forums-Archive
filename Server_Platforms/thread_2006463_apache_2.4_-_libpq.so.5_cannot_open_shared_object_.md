---
title: "apache 2.4 - libpq.so.5: cannot open shared object file"
date: 2012-06-19
forum: Server Platforms
---

### Post by A2llex on 2012-06-19
hey, i've compiled Apache2.4 from source, and everything worked well, and suddenly if i try to restart apache:

httpd: Syntax error on line 146 of /usr/local/apache2/conf/httpd.conf: Cannot load /usr/local/apache2/modules/libphp5.so into server: libpq.so.5: cannot open shared 
object file: No such file or directory

idk it's because i did this? 

 apt-get remove --purge mysql-common

Remove: libapr1:amd64 (1.4.6-1), libaprutil1-ldap:amd64 (1.3.12+dfsg-3), libapr1-dev:amd64 (1.4.6-1), apache2-utils:amd64 (2.2.22-1ubuntu1), apache2.2-common:amd64 (2.2.22-1ubuntu1), libaprutil1-dbd-sqlite3:amd64 (1.3.12+dfsg-3), mysql-client-core-5.5:amd64 (5.5.22-0ubuntu1), apache2.2-bin:amd64 (2.2.22-1ubuntu1), uuid-dev:amd64 (2.20.1-1ubuntu3), libpq-dev:amd64 (9.1.3-2), libsqlite3-dev:amd64 (3.7.9-2ubuntu1), libpq5:amd64 (9.1.3-2), libaprutil1:amd64 (1.3.12+dfsg-3)

---

### Post by A2llex on 2012-06-19
> **A2llex said:**
> hey, i've compiled Apache2.4 from source, and everything worked well, and suddenly if i try to restart apache:

httpd: Syntax error on line 146 of /usr/local/apache2/conf/httpd.conf: Cannot load /usr/local/apache2/modules/libphp5.so into server: libpq.so.5: cannot open shared 
object file: No such file or directory

idk it's because i did this? 

 apt-get remove --purge mysql-common

Remove: libapr1:amd64 (1.4.6-1), libaprutil1-ldap:amd64 (1.3.12+dfsg-3), libapr1-dev:amd64 (1.4.6-1), apache2-utils:amd64 (2.2.22-1ubuntu1), apache2.2-common:amd64 (2.2.22-1ubuntu1), libaprutil1-dbd-sqlite3:amd64 (1.3.12+dfsg-3), mysql-client-core-5.5:amd64 (5.5.22-0ubuntu1), apache2.2-bin:amd64 (2.2.22-1ubuntu1), uuid-dev:amd64 (2.20.1-1ubuntu3), libpq-dev:amd64 (9.1.3-2), libsqlite3-dev:amd64 (3.7.9-2ubuntu1), libpq5:amd64 (9.1.3-2), libaprutil1:amd64 (1.3.12+dfsg-3)


ok i solved this already :)

i compiled php --with-pgsql and mod php was loading shared library that didn't exist.

---

