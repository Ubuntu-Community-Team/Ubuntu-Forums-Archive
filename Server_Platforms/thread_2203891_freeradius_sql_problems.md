---
title: "freeradius sql problems"
date: 2014-02-05
forum: Server Platforms
---

### Post by Gareth_2007 on 2014-02-05
Evening all,

having a few problems with freeradius

here's my log output:

```
Wed Feb 5 22:40:05 2014 : Info: Ready to process requests.
Wed Feb 5 22:40:05 2014 : Info: ... adding new socket proxy address * port 44494
Wed Feb 5 22:40:05 2014 : Info: Loaded virtual server inner-tunnel
Wed Feb 5 22:40:05 2014 : Info: Loaded virtual server 
Wed Feb 5 22:40:05 2014 : Info: rlm_sql (sql): Connected new DB handle, #4
Wed Feb 5 22:40:05 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Wed Feb 5 22:40:05 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Wed Feb 5 22:40:05 2014 : Info: rlm_sql (sql): Connected new DB handle, #3
Wed Feb 5 22:40:05 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #3
Wed Feb 5 22:40:05 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #3
Wed Feb 5 22:40:05 2014 : Info: rlm_sql (sql): Connected new DB handle, #2
Wed Feb 5 22:40:05 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #2
Wed Feb 5 22:40:05 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #2
Wed Feb 5 22:40:05 2014 : Info: rlm_sql (sql): Connected new DB handle, #1
Wed Feb 5 22:40:05 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #1
Wed Feb 5 22:40:05 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #1
Wed Feb 5 22:40:05 2014 : Info: rlm_sql (sql): Connected new DB handle, #0
Wed Feb 5 22:40:04 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Wed Feb 5 22:40:04 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Wed Feb 5 22:40:04 2014 : Info: rlm_sql (sql): Attempting to connect to raddbuser@localhost:/radiusdb
Wed Feb 5 22:40:04 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Wed Feb 5 22:40:03 2014 : Error: Failed to load virtual server 
Wed Feb 5 22:40:03 2014 : Error: /etc/freeradius/sites-enabled/default[69]: Errors parsing authorize section. 
Wed Feb 5 22:40:03 2014 : Error: /etc/freeradius/sites-enabled/default[177]: Failed to load module "sql".
Wed Feb 5 22:40:03 2014 : Error: /etc/freeradius/sql.conf[22]: Instantiation failed for module "sql"
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Closing sqlsocket 0
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Closing sqlsocket 1
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Closing sqlsocket 2
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Closing sqlsocket 3
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Closing sqlsocket 4
Wed Feb 5 22:40:03 2014 : Error: Failed to load clients from SQL.
Wed Feb 5 22:40:03 2014 : Error: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 0
Wed Feb 5 22:40:03 2014 : Error: rlm_sql (sql): Failed to connect DB handle #0
Wed Feb 5 22:40:03 2014 : Error: rlm_sql_mysql: Mysql error 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Wed Feb 5 22:40:03 2014 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server raddbuser@localhost:radiusdb
Wed Feb 5 22:40:03 2014 : Error: Failed to load virtual server 
Wed Feb 5 22:40:03 2014 : Error: /etc/freeradius/sites-enabled/default[69]: Errors parsing authorize section. 
Wed Feb 5 22:40:03 2014 : Error: /etc/freeradius/sites-enabled/default[177]: Failed to load module "sql".
Wed Feb 5 22:40:03 2014 : Error: /etc/freeradius/sql.conf[22]: Instantiation failed for module "sql"
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Closing sqlsocket 0
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Closing sqlsocket 1
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Closing sqlsocket 2
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Closing sqlsocket 3
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Closing sqlsocket 4
Wed Feb 5 22:40:03 2014 : Error: Failed to load clients from SQL.
Wed Feb 5 22:40:03 2014 : Error: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 0
Wed Feb 5 22:40:03 2014 : Error: rlm_sql (sql): Failed to connect DB handle #0
Wed Feb 5 22:40:03 2014 : Error: rlm_sql_mysql: Mysql error 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Wed Feb 5 22:40:03 2014 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server raddbuser@localhost:radiusdb
Wed Feb 5 22:40:03 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Attempting to connect to raddbuser@localhost:/radiusdb
Wed Feb 5 22:40:03 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Attempting to connect to raddbuser@localhost:/radiusdb
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Wed Feb 5 22:40:03 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
```

any suggestions?

many thanks
gareth

---

### Post by nerdtron on 2014-02-06
Seems like you are having problems on freeradius to use sql as database. Have a look at the procedures here for granting freeradius access to database.
[http://www.howtoforge.com/setting-up-a-freeradius-based-aaa-server-with-mysql-and-management-with-daloradius](http://www.howtoforge.com/setting-up-a-freeradius-based-aaa-server-with-mysql-and-management-with-daloradius)

---

