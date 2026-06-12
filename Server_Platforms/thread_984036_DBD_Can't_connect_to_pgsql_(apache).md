---
title: "DBD: Can't connect to pgsql (apache)"
date: 2008-11-16
forum: Server Platforms
---

### Post by MDSmith2 on 2008-11-16
I am trying to use mod_auth_dbd to password a directory on my personal server, and it will ask for the user/password, but once I press enter, I get a 500 Internal Server error.
this is the log for the time of trying to log in: 
```
[Sun Nov 16 09:26:30 2008] [error] (20014)Internal error: DBD: Can't connect to pgsql
[Sun Nov 16 09:26:30 2008] [error] (20014)Internal error: DBD: failed to initialise
[Sun Nov 16 09:26:30 2008] [error] (20014)Internal error: DBD: Can't connect to pgsql
[Sun Nov 16 09:26:30 2008] [error] (20014)Internal error: DBD: failed to initialise
[Sun Nov 16 09:26:30 2008] [error] (20014)Internal error: DBD: Can't connect to pgsql
[Sun Nov 16 09:26:30 2008] [error] (20014)Internal error: DBD: failed to initialise
[Sun Nov 16 09:26:30 2008] [error] (20014)Internal error: DBD: Can't connect to pgsql
[Sun Nov 16 09:26:30 2008] [error] (20014)Internal error: DBD: failed to initialise
[Sun Nov 16 09:26:30 2008] [error] (20014)Internal error: DBD: Can't connect to pgsql
[Sun Nov 16 09:26:30 2008] [error] (20014)Internal error: DBD: failed to initialise
[Sun Nov 16 09:26:30 2008] [notice] Apache/2.2.8 (Ubuntu) mod_auth_pgsql/2.0.3 PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sun Nov 16 09:26:40 2008] [error] (20014)Internal error: DBD: Can't connect to pgsql
[Sun Nov 16 09:26:40 2008] [error] (20014)Internal error: DBD: failed to initialise
[Sun Nov 16 09:26:46 2008] [warn] [client 127.0.0.1] [mod_auth_pgsql.c] - missing configuration parameters
[Sun Nov 16 09:26:46 2008] [error] (20014)Internal error: DBD: Can't connect to pgsql
[Sun Nov 16 09:26:46 2008] [error] (20014)Internal error: DBD: failed to initialise
[Sun Nov 16 09:26:46 2008] [error] [client 127.0.0.1] Error looking up admin in database
```
and this is my auth_dbd.conf:
```
# mod_dbd configuration
DBDriver pgsql
DBDParams "dbhost=localhost dbname=apache2auth dbport=5432 user=apache2auth password=********"

DBDMin  4
DBDKeep 8
DBDMax  20
DBDExptime 300

<Directory /var/www/files>
  # core authentication and mod_auth_basic configuration
  # for mod_authn_dbd
  AuthType Basic
  AuthName "This directory requires a username and password"
  AuthBasicProvider dbd

  # core authorization configuration
  Require valid-user

  # mod_authn_dbd SQL query to authenticate a user
  AuthDBDUserPWQuery  "SELECT password FROM authn WHERE username = %s"
</Directory>

```
Any clues? Thanks

---

