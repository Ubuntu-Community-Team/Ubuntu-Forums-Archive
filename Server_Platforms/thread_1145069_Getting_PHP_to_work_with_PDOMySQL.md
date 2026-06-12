---
title: "Getting PHP to work with PDO/MySQL"
date: 2009-05-01
forum: Server Platforms
---

### Post by kepardue on 2009-05-01
Seems that PHP doesn't have support for PDO on my system (which is 8.04 LTS).  I installed PDO and the Mysql connector for it, and I can actually get my database to successfully connnect.  And yet, whenever I run a query on it I get a Call to a member function fetch() on a non-object.

I've been testing this locally on my Mac, which is running MAMP, wit no problems.

Relevant info from the phpinfo():

**PHP Version 5.2.4-2ubuntu5.6**

**additional .ini files parsed**
/etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini

**PDO**
PDO support	enabled
PDO drivers 	mysql

**pdo_mysql**
PDO Driver for MySQL, client library version	5.0.51a

**mysql**
MySQL Support	enabled
Active Persistent Links 	0
Active Links 	0
Client API version 	5.0.51a
MYSQL_MODULE_TYPE 	external
MYSQL_SOCKET 	/var/run/mysqld/mysqld.sock
MYSQL_INCLUDE 	-I/usr/include/mysql
MYSQL_LIBS 	-L/usr/lib -lmysqlclient

Directive	Local Value	Master Value
mysql.allow_persistent	On	On
mysql.connect_timeout	60	60
mysql.default_host	no value	no value
mysql.default_password	no value	no value
mysql.default_port	no value	no value
mysql.default_socket	no value	no value
mysql.default_user	no value	no value
mysql.max_links	Unlimited	Unlimited
mysql.max_persistent	Unlimited	Unlimited
mysql.trace_mode	Off	Off

---

