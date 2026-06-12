---
title: "Asterisk realtime problem &quot;Table cc_sip_buddies not found in database&quot;"
date: 2010-11-25
forum: Server Platforms
---

### Post by cjav on 2010-11-25
Hi,

I'm trying to configure realtime in my asterisk server and I'm running into this problem:
```
res_config_mysql.c: Table cc_sip_buddies not found in database.  This table should exist if you're using realtime.
res_config_mysql.c: Table cc_iax_buddies not found in database.  This table should exist if you're using realtime.
```

Some output and configuration files:
extconfig.conf
```
sipusers => mysql,mya2billing,cc_sip_buddies
sippeers => mysql,mya2billing,cc_sip_buddies
iaxusers => mysql,mya2billing,cc_iax_buddies
iaxpeers => mysql,mya2billing,cc_iax_buddies
```
res_mysql.conf
```
[general]
dbhost = 127.0.0.1
dbname = mya2billing
dbuser = a2billinguser
dbpass = **********
dbport = 3306
dbsock = /tmp/mysql.sock
requirements=warn ; or createclose or createchar

```
```
*CLI> core show config mappings
Config Engine: mysql
===> iaxpeers (db=mya2billing, table=cc_iax_buddies)
===> iaxusers (db=mya2billing, table=cc_iax_buddies)
===> sippeers (db=mya2billing, table=cc_sip_buddies)
===> sipusers (db=mya2billing, table=cc_sip_buddies)

Config Engine: sqlite

Config Engine: curl

```
```
*CLI> realtime mysql status
general connected to mya2billing@127.0.0.1, port 3306 with username a2billinguser for 0 seconds.
*CLI> realtime load iaxuser name **********
No rows found matching search criteria.
```

I had made sure cc_sip_buddies and cc_iax_buddies are in the database, they are, and they have some entries, don't know what could be going wrong here.
```
mysql -u a2billinguser -p*********** mya2billing
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 139
Server version: 5.1.49-1ubuntu8.1 (Ubuntu)

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> select * from cc_iax_buddies;
+----+------------+------------+-------------+------------+----------+----------+-----------+-----------+---------+----------+------+--------+------+------+---------+------------+--------+------------+----------+--------------------+------------+--------+-------+----------+------------+---------------+--------------+------------+--------+--------+------------+---------+----------+------+------------+------------+----------+--------------+-------------------+---------------+------------------+---------------+------------------+----------+------+--------+------------------+----------------+-----------------------------+
| id | id_cc_card | name       | accountcode | regexten   | amaflags | callerid | context   | DEFAULTip | host    | language | deny | permit | mask | port | qualify | secret     | type   | username   | disallow | allow              | regseconds | ipaddr | trunk | dbsecret | regcontext | sourceaddress | mohinterpret | mohsuggest | inkeys | outkey | cid_number | sendani | fullname | auth | maxauthreq | encryption | transfer | jitterbuffer | forcejitterbuffer | codecpriority | qualifysmoothing | qualifyfreqok | qualifyfreqnotok | timezone | adsi | setvar | requirecalltoken | maxcallnumbers | maxcallnumbers_nonvalidated |
+----+------------+------------+-------------+------------+----------+----------+-----------+-----------+---------+----------+------+--------+------+------+---------+------------+--------+------------+----------+--------------------+------------+--------+-------+----------+------------+---------------+--------------+------------+--------+--------+------------+---------+----------+------+------------+------------+----------+--------------+-------------------+---------------+------------------+---------------+------------------+----------+------+--------+------------------+----------------+-----------------------------+
|  1 |         12 | ********** | **********  | ********** | billing  |          | a2billing | NULL      | dynamic | NULL     |      | NULL   |      |      | no      | ********** | friend | ********** |          | ulaw,alaw,gsm,g729 |          0 |        | no    |          |            |               |              |            |        |        |            |         |          |      |            |            |          |              |                   |               |                  |               |                  |          |      |        |                  |                |                             |
|  2 |         13 | ********** | **********  | ********** | billing  |          | a2billing | NULL      | dynamic | NULL     |      | NULL   |      |      | no      | ********** | friend | ********** |          | ulaw,alaw,gsm,g729 |          0 |        | no    |          |            |               |              |            |        |        |            |         |          |      |            |            |          |              |                   |               |                  |               |                  |          |      |        |                  |                |                             |
+----+------------+------------+-------------+------------+----------+----------+-----------+-----------+---------+----------+------+--------+------+------+---------+------------+--------+------------+----------+--------------------+------------+--------+-------+----------+------------+---------------+--------------+------------+--------+--------+------------+---------+----------+------+------------+------------+----------+--------------+-------------------+---------------+------------------+---------------+------------------+----------+------+--------+------------------+----------------+-----------------------------+
2 rows in set (0.00 sec)

```

I'm using Ubuntu Server Maverick 10.10 with Asterisk 1.6 from the repos.

Any help will be highly appreciated 
Carlos

---

### Post by areski on 2011-05-21
Hi,

in /etc/asterisk/res_mysql.conf, you have 2 sections, one called a2billing to connect to the a2billing database.

Therefore in your extconfig.conf, you need to set the realtime setting to use the a2billing database.

So replace by :
[settings]
sipusers => mysql,a2billing,cc_sip_buddies
sippeers => mysql,a2billing,cc_sip_buddies
iaxusers => mysql,a2billing,cc_iax_buddies
iaxpeers => mysql,a2billing,cc_iax_buddies
;a2billing doesn't provide extensions configuration
;extensions => mysql,general,cc_sip_buddies 


Yours,
/Areski
[http://www.star2billing.com]("http://www.star2billing.com")

---

