---
title: "collectd 4.10.1"
date: 2010-11-06
forum: Server Platforms
---

### Post by kaushalshriyan on 2010-11-06
Hi,

I am using collectd 4.10.1 on Ubuntu 8.04 server. I am following
[http://collectd.org/wiki/index.php/Plugin:MySQL](http://collectd.org/wiki/index.php/Plugin:MySQL).
I get```
 [2010-11-03 01:49:15] mysql_real_connect failed: Access denied
for user 'root'@'localhost' (using password: NO) in the
collectd-debug.log. Please advice.

My configs are as below

<Plugin "mysql">
       <Database "SMSPAY">
               User "nagios"
               Password ""
               Socket "/var/run/mysqld/mysqld1.sock"
       </Database>
       <Database "SMSIN">
               User "nagios"
               Password ""
               Socket "/var/run/mysqld/mysqld2.sock"
       </Database>
</Plugin>


mysql -u nagios -S /var/run/mysqld/mysqld1.sock -DSMSPAY
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 89393
Server version: 5.0.51a-3ubuntu5.4-log (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show tables;
+-------------------+
| Tables_in_SMSPAY  |
+-------------------+
| ACCOUNTS          |
| AMT_MISMATCH_LOG  |
| APICALLAUDITTRAIL |
| APPDEVELOPER      |
| APPINFO           |
| BANKS             |
| BILLING_LOG       |
| CASH_DETAILS      |
| CHEQUE_DETAILS    |
| DEPOSIT_DETAILS   |
| ITZCASH_DETAILS   |
| MIGRATE_LOG       |
| PAYSEAL_DETAILS   |
| PAYTRONIC_DETAILS |
| TECHPRO_DETAILS   |
| TRANSACTIONS      |
| USERLOGIN         |
| USERS             |
| ZIPCASH_DETAILS   |
+-------------------+
19 rows in set (0.00 sec)

mysql>
#mysql -u nagios -S /var/run/mysqld/mysqld2.sock -DSMSIN
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 92810
Server version: 5.0.51a-3ubuntu5.4-log (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show tables;
+-----------------+
| Tables_in_SMSIN |
+-----------------+
| InURL           |
| InURLMapping    |
| InURLMappingOld |
| MsgNew          |
| TmpMsgIn        |
+-----------------+
5 rows in set (0.00 sec)

mysql>
```

---

