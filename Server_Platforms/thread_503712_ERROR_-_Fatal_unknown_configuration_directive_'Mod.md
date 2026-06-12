---
title: "ERROR: - Fatal: unknown configuration directive 'ModulePath' ... ?"
date: 2007-07-18
forum: Server Platforms
---

### Post by asteriskese on 2007-07-18
I've installed **proftpd-1.3.0a.tar.gz** on my computer, proftpd has running and i tested by system account (**abc/abc**). It's running OK. Now i want to manage account by MySQL database. 

================================
**MySQL 5.0.14**
MYSQL_HOME=/usr/local/mysql/
--------------------------------------/bin
--------------------------------------/include
--------------------------------------/info
--------------------------------------/libexec
--------------------------------------/man
--------------------------------------/mysql-test
--------------------------------------/share
--------------------------------------/mysql-bench
--------------------------------------/var



**proftpd-1.3.0a.tar.gz**
PROFTPD_HOME=/usr/local/proftpd/
--------------------------------------------/bin
--------------------------------------------/etc
--------------------------------------------/libexec
--------------------------------------------/man
--------------------------------------------/sbin
--------------------------------------------/var

**Installation details:**

#./configure --prefix=/usr/local/proftpd \
--with-modules=mod_sql:mod_sql_mysql:mod_quotatab:mod_quotatab_sql \
--with-includes=/usr/include/mysql \
--with-libraries=/usr/lib/mysql
#make
#make install

Running proftpd:
#**/usr/local/proftpd/sbin/proftpd**
Login successfull with system account.

Now, i config proftpd to manage by MySQL database:
(viewing files attachment)

When i run proftpd:
ERR: 
- Fatal: **unknown configuration directive 'ModulePath**' on line 4 of '/usr/local/proftpd/etc/modules.conf'

Anybody help me? 

Thanks for reading.

**[http://www.harmonysoft.com.vn/tinh_cx/proftpd.zip]("http://www.harmonysoft.com.vn/tinh_cx/proftpd.zip")**

---

