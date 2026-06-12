---
title: "Dovecot: Unknown passdb driver 'mysql'"
date: 2008-07-06
forum: Server Platforms
---

### Post by asmweb on 2008-07-06
I'm havin problems making dovecot running... I compiled it from the source as the RHEL4 had old version on its repos and now I got version 1.0.3
I compiled it like this:

./configure --with-mysql
make
make install

all seemed to work fine not errors on compilation. When i try to send as a try I get this error:

Unknown passdb driver 'mysql' (typo, or Dovecot was built without support for it? Check with dovecot --build-options)

root@domain ~]# usr/local/sbin/dovecot --build-options
Build options: ioloop=poll notify=dnotify ipv6 openssl
SQL drivers: mysql
Passdb: checkpassword passwd passwd-file shadow sql
Userdb: checkpassword passwd prefetch passwd-file sql static


I can not understand why of that... on the other hand I have mysql-devel installed.

anyone has any idea?
thanks

---

