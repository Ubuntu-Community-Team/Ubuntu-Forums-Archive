---
title: "Mysqld (5.1) won't start after Karmik Koala upgrade"
date: 2009-10-30
forum: Server Platforms
---

### Post by koala-server on 2009-10-30
# /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [fail]

Here is syslog contents: [http://pastie.org/677269](http://pastie.org/677269)

And nothing in mysql.log or mysql.err

> # uname -a
Linux mycomp 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

# cat /etc/issue
Ubuntu 9.10 \n \l

---

### Post by karlson on 2009-10-30
> **koala-server said:**
> # /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [fail]

Here is syslog contents: [http://pastie.org/677269](http://pastie.org/677269)

And nothing in mysql.log or mysql.err


Based on the log you posted:

```

Oct 30 22:03:20 mycomp mysqld: 091030 22:03:20 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.

```

Have you run mysql_upgrade?

---

### Post by koala-server on 2009-10-30
> **karlson said:**
> Based on the log you posted:

```

Oct 30 22:03:20 mycomp mysqld: 091030 22:03:20 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.

```Have you run mysql_upgrade?

sure:

# mysql_upgrade
Looking for 'mysql' as: mysql
Looking for 'mysqlcheck' as: mysqlcheck
Running 'mysqlcheck' with connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock'
mysqlcheck: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) when trying to connect
FATAL ERROR: Upgrade failed

---

### Post by runeg on 2009-10-30
This worked for me;

In your /etc/mysql/my.cnf locate the ```
skip-bdb
``` part and comment that out by placing a hashtag (#) in front of it. Then do a ```
apt-get -f install
``` and your upgrade should complete.

I had to do this after I upgraded from 9.04 server to 9.10 server.

HTH!

Regards,
RuneG

---

### Post by koala-server on 2009-10-30
Gr8, solved! :)
Thanks!

---

### Post by pokapeski on 2009-10-30
thanks runeg!

---

### Post by runeg on 2009-10-31
No problem! 

--
RuneG

---

### Post by gorvas on 2009-11-01
Thanks for the help!

---

### Post by johnnybirdman on 2010-01-20
still good information.
Thanks,
J.

---

### Post by whit on 2011-03-09
Yup, commenting out "skip-bdb" is crucial if you've kept your old my.cnf - as I had. Thanks.

---

