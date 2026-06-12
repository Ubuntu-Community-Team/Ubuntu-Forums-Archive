---
title: "[SOLVED] OpenLDAP and unixodbc won't connect"
date: 2008-07-19
forum: Server Platforms
---

### Post by beniwtv on 2008-07-19
Hi all,

I'm trying to configure OpenLDAP to use the back_sql backend, but the following error appears:

```
==>backsql_get_db_conn()
==>backsql_open_db_handle()
backsql_open_db_handle(): SQLConnect() to database "MySQL" failed.
Return code: -1
   nativeErrCode=0 SQLengineState=IM002 msg="[unixODBC][Driver Manager]Data source name not found, and no default driver specified"
backsql_db_open(): connection failed, exiting
backend_startup_one: bi_db_open failed! (1)

```

However, if I use "isql MySQL", it works without any problems.

/etc/ldap/slapd.conf:

```
backend sql

database        sql
# This following is for the sample database as it installs
suffix          "ou=employees,dc=rhino-tde,dc=net"
dbname          MySQL
dbuser          myuser
dbpasswd	mypass
subtree_cond    "ldap_entries.dn LIKE CONCAT('%',?)"
insentry_query  "INSERT INTO ldap_entries (dn,oc_map_id,parent,keval) VALUES (?,?,?,?)"
has_ldapinfo_dn_ru	no
subordinate

```

/etc/odbc.ini:

```
[ODBC Data Sources]
MySQL = MySQL connection

[MySQL]
DSN 		    = ldap
Description         = MySQL connection
Driver              = MySQL
Database            = ldap
Server              = localhost
Port                = 3306
Socket              =
User		    = myuser
Password            = mypass

```

/etc/odbcinst.ini:

```
[MySQL]
Description     = MySQL driver
Driver          = /usr/lib/odbc/libmyodbc.so
Setup           = /usr/lib/odbc/libodbcmyS.so
CPTimeout	=
CPReuse		=

```

I'm on Hardy 8.04 server.

Judging that it works with isql, I can only suppose slapd doesn't find the odbc.ini file.

I've tried also to set to ODBCINI environment variable, to no avail.

Anyone using back_sql?

NOTE: I saw slapd has been changed from iODBC to unixODBC. In my Debian machine, I'm still using iODBC, and it works great there.

---

### Post by beniwtv on 2008-07-19
Well, answering my own post: :)

The problem was Apparmor, which didn't give permissions to slapd for reading the odbc config.

If someone runs into the same problem, here is how to solve it:

Open /etc/apparmor.d/usr.sbin.slapd and add:

```

# we need odbc
/etc/odbc.ini r,
/etc/odbcinst.ini r,
/var/run/mysqld/mysqld.sock w,
```

Then reload apparmor:  sudo /etc/init.d/apparmor reload

Cheers,

---

### Post by void_void on 2009-11-05
[B][SIZE="6"]

i am trapped here...
followed you and getting following error[/SIZE][/B]

acksql_db_open(): DN match search SQL condition not specified (use "dn_match_cond" directive in slapd.conf); preparing default
backsql_db_open(): setting "upper(ldap_entries.dn)=upper(?)" as default "dn_match_cond"
backsql_db_open(): objectclass mapping SQL statement not specified (use "oc_query" directive in slapd.conf)
backsql_db_open(): setting "SELECT id,name,keytbl,keycol,create_proc,delete_proc,expect_return FROM ldap_oc_mappings" by default
backsql_db_open(): attribute mapping SQL statement not specified (use "at_query" directive in slapd.conf)
backsql_db_open(): setting "SELECT name,sel_expr,from_tbls,join_where,add_proc,delete_proc,param_order,expect_return,sel_expr_u FROM ldap_attr_mappings WHERE oc_map_id=?" by default
backsql_db_open(): entry deletion SQL statement not specified (use "delentry_stmt" directive in slapd.conf)
backsql_db_open(): setting "DELETE FROM ldap_entries WHERE id=?" by default
backsql_db_open(): entry deletion SQL statement not specified (use "renentry_stmt" directive in slapd.conf)
backsql_db_open(): setting "UPDATE ldap_entries SET dn=?,parent=?,keyval=? WHERE id=?" by default
backsql_db_open(): objclasses deletion SQL statement not specified (use "delobjclasses_stmt" directive in slapd.conf)
backsql_db_open(): setting "DELETE FROM ldap_entry_objclasses WHERE entry_id=?" by default
==>backsql_get_db_conn()
==>backsql_open_db_handle()
backsql_open_db_handle(): SQLConnect() to database "PgSQL" failed.
Return code: -1
   nativeErrCode=0 SQLengineState=01000 msg="[unixODBC][Driver Manager]Can't open lib '/usr/local/lib/psqlodbcw.so' : /usr/local/lib/psqlodbcw.so: cannot open shared object file: Permission denied"
backsql_db_open(): connection failed, exiting
backend_startup_one: bi_db_open failed! (1)
slapd shutdown: initiated
==>backsql_db_close()
<==backsql_db_close()
slapd destroy: freeing system resources.
==>backsql_db_destroy()
==>backsql_free_db_env()
<==backsql_free_db_env()
==>destroy_schema_map()
<==destroy_schema_map()
<==backsql_db_destroy()
slapd stopped.

---

### Post by void_void on 2009-11-05
permission is already given to that file..

---

### Post by beniwtv on 2009-11-05
Seems like unixODBC is not able to open/find the file /usr/local/lib/psqlodbcw.so.

Check permissions for that file - and don't forget to look into syslog for AppArmor messages.

---

