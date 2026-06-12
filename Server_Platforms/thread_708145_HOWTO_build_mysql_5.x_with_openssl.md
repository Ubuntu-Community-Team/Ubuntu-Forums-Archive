---
title: "HOWTO: build mysql 5.x with openssl"
date: 2008-02-26
forum: Server Platforms
---

### Post by anomalous_underdog on 2008-02-26
I've found out that the default mysql binaries that come in the package respositories aren't compiled with openssl support.

Look at this first:
[https://help.ubuntu.com/community/MYSQL5FromSource](https://help.ubuntu.com/community/MYSQL5FromSource)

You might want to look at this too:
[http://dev.mysql.com/doc/refman/5.0/en/secure-using-ssl.html](http://dev.mysql.com/doc/refman/5.0/en/secure-using-ssl.html)

Prior to compiling, make sure libssl-dev is installed, and, of course, remove your old mysql-server.

In the configuration part, instead of using the one provided by the wiki article, the proper arguments would be:
```

./configure \
--prefix=/usr/local/mysql \
--with-mysqld-user=mysql \
--without-debug \
**--enable-thread-safe-client \**
--disable-shared \
--localstatedir=/usr/local/mysql/data \
--with-extra-charsets=none \
--enable-assembler \
--with-unix-socket-path=/tmp/mysql.socket \
**--with-openssl**
```

(remove "--with-client-ldflags=-all-static \" and "--with-mysqld-ldflags=-all-static \" as mysql requires no static linking if openssl is enabled)


I needed to run:
```
sudo chmod 775 /usr/local/mysql
```

As for the:
```
/usr/local/mysql/bin/mysqld_safe -user=mysql&
```
I needed to run that with sudo


Other than that, the directions provided by the wiki article works.

I don't understand why the default binaries aren't compiled with ssl support by default.

---

### Post by anomalous_underdog on 2008-02-26
As for testing the ssl using self-signed certificates, this tutorial worked for me:
[http://www.waterlovinghead.com/MysqlSSL](http://www.waterlovinghead.com/MysqlSSL)

---

### Post by anomalous_underdog on 2008-02-27
ok, now I need help.

I got as far as:

show variables like 'have_openssl';
```
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| have_openssl  | YES   |
+---------------+-------+
```

but \s gives me:

```
Connection id:          3
Current database:
**SSL:                    Not in use**
Current pager:          stdout
Using outfile:          ''
Using delimiter:        ;
Server version:         5.0.51a-log Source distribution
Protocol version:       10
Connection:             Localhost via UNIX socket
Server characterset:    latin1
Db     characterset:    latin1
Client characterset:    latin1
Conn.  characterset:    latin1
UNIX socket:            /var/run/mysqld/mysqld.sock
Uptime:                 13 min 29 sec
```

the mysql client variables:
```
ssl                               TRUE
ssl-ca                            /home/ferdi/mysql/mysql-ca-cert.pem
ssl-capath                        (No default value)
ssl-cert                          /home/ferdi/mysql/mysql-client-cert.pem
ssl-cipher                        DHE-RSA-AES256-SHA
ssl-key                           /home/ferdi/mysql/mysql-client-key.pem
ssl-verify-server-cert            FALSE
```

What other info do I need to show you guys?

Hope someone can help

---

