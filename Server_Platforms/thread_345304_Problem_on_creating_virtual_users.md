---
title: "Problem on creating virtual users"
date: 2007-01-24
forum: Server Platforms
---

### Post by satimis on 2007-01-24
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64


I followed following document to create Virtual Users And Domains

[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier)

According to;
1. Install Postfix, Courier, Saslauthd, MySQL, phpMyAdmin
This can all be installed with one single command:```

apt-get install postfix postfix-mysql postfix-doc mysql-client
mysql-server courier-authdaemon courier-authmysql courier-pop
courier-pop-ssl courier-imap courier-imap-ssl postfix-tls libsasl2
libsasl2-modules libsasl2-modules-sql sasl2-bin libpam-mysql 
openssl phpmyadmin (1 line!)
```

Because some packages have been installed already and I don't expect to overwrite the existing config files on reinstalling some of them.  There I performed follows;

$ dpkg -al | grep postfix```

ii  postfix                                          2.2.10-1ubuntu0.1              A high-performance mail transport agent

```

$ dpkg -al | grep mysql```

ii  libapache2-mod-auth-mysql                        4.3.9-2ubuntu3              Apache 2 module for MySQL authentication
ii  libdbd-mysql-perl                                3.0002-2build1              A Perl5 database interface to the MySQL data
ii  libmysqlclient12                                 4.0.24-10ubuntu2              mysql database client library
ii  libmysqlclient12-dev                             4.0.24-10ubuntu2              mysql database development files
ii  libmysqlclient15off                              5.0.22-0ubuntu6.06.2              mysql database client library
ii  mysql-admin                                      1.1.6-1build1              GUI tool for intuitive MySQL administration
ii  mysql-admin-common                               1.1.6-1build1              Architecture independent files for MySQL Adm
ii  mysql-client                                     5.0.22-0ubuntu6.06.2              mysql database client (current version)
ii  mysql-client-5.0                                 5.0.22-0ubuntu6.06.2              mysql database client binaries
ii  mysql-common                                     5.0.22-0ubuntu6.06.2              mysql database common files (e.g. /etc/mysql
ii  mysql-server                                     5.0.22-0ubuntu6.06.2              mysql database server (current version)
ii  mysql-server-5.0                                 5.0.22-0ubuntu6.06.2              mysql database server binaries
ii  php5-mysql                                       5.1.2-1ubuntu3.4              MySQL module for php5
ii  php5-mysqli                                      5.1.2-1ubuntu3.4              MySQL Improved module for php5
ii  python-mysqldb                                   1.2.1c3-4ubuntu4              A Python interface to MySQL
ii  python2.4-mysqldb                                1.2.1c3-4ubuntu4              A Python interface to MySQL

```

$ dpkg -al | grep postfix-mysql
$ dpkg -al | grep postfix-doc
both no printout

$ dpkg -al | grep mysql-client```

ii  mysql-client                                     5.0.22-0ubuntu6.06.2              mysql database client (current version)
ii  mysql-client-5.0                                 5.0.22-0ubuntu6.06.2              mysql database client binaries

```

$ dpkg -al | grep mysql-server```

ii  mysql-server                                     5.0.22-0ubuntu6.06.2              mysql database server (current version)
ii  mysql-server-5.0                                 5.0.22-0ubuntu6.06.2              mysql database server binaries

```

$ dpkg -al | grep courier```

ii  courier-authdaemon                               0.47-13ubuntu5.1              Courier Mail Server - Authentication daemon
ii  courier-base                                     0.47-13ubuntu5.1              Courier Mail Server - Base system
ii  courier-imap                                     3.0.8-13ubuntu5.1              Courier Mail Server - IMAP server
ii  courier-maildrop                                 0.47-13ubuntu5.1              Courier Mail Server - Mail delivery agent
ii  courier-ssl                                      0.47-13ubuntu5.1              Courier Mail Server - SSL/TLS Support

```

$ dpkg -al | grep courier-pop
no printout

$ dpkg -al | grep libsasl2```

ii  libsasl2                                         2.1.19.dfsg1-0.1ubuntu2              Authentication abstraction library
ii  libsasl2-modules                                 2.1.19.dfsg1-0.1ubuntu2              Pluggable Authentication Modules for SASL

```

$ dpkg -al | grep sasl2```

ii  libsasl2                                         2.1.19.dfsg1-0.1ubuntu2              Authentication abstraction library
ii  libsasl2-modules                                 2.1.19.dfsg1-0.1ubuntu2              Pluggable Authentication Modules for SASL
ii  sasl2-bin                                        2.1.19.dfsg1-0.1ubuntu2              Programs for manipulating the SASL users dat

```

$ dpkg -al | grep libpam```

ii  libpam-foreground                                0.3              create lockfiles describing which users own
ii  libpam-modules                                   0.79-3ubuntu14              Pluggable Authentication Modules for PAM
ii  libpam-runtime                                   0.79-3ubuntu14              Runtime support for the PAM library
ii  libpam0g                                         0.79-3ubuntu14              Pluggable Authentication Modules library

```

$ dpkg -al | grep openssl```

ii  openssl                                          0.9.8a-7ubuntu0.3              Secure Socket Layer (SSL) binary and related
ii  python-pyopenssl                                 0.6-2ubuntu3              Python wrapper around the OpenSSL library (d
ii  python2.4-pyopenssl                              0.6-2ubuntu3              Python wrapper around the OpenSSL library, e
ii  ssl-cert                                         1.0.13              Simple debconf wrapper for openssl

```

$ dpkg -al | grep phpmyadmin
no printout

I found following packages not installed yet;```

postfix-mysql postfix-doc courier-authmysql courier-pop 
courier-pop-ssl courier-imap-ssl postfix-tls libsasl2-modules-sql 
libpam-mysql phpmyadmin

```

$ sudo apt-get install postfix-mysql postfix-doc courier-authmysql courier-pop courier-pop-ssl courier-imap-ssl postfix-tls libsasl2-modules-sql libpam-mysql phpmyadmin```

Reading package lists... Done
Building dependency tree... Done
Package postfix-tls is a virtual package provided by:
  postfix 2.2.10-1ubuntu0.1
You should explicitly select one to install.
E: Package postfix-tls has no installation candidate

```

Please advise how to proceed.  TIA


Furthermore on LAN there is no workstation connected.  What front-end/GUI package I need to install to send mails instead of running the command line "telnet localhost 25 etc."

Evolution or there are others?  TIA


B.R.
satimis

---

