---
title: "mysql prob with debian-sys-maint"
date: 2006-10-05
forum: Server Platforms
---

### Post by reutel on 2006-10-05
Howdy,

I've changed the access of debian-sys-maint to @127.0.0.1 in myadmin, and debian.cnf, but now I get this error:

Got a failure from command:
cat /usr/share/mysql/mysql_fix_privilege_tables.sql | /usr/bin/mysql --no-defaults --force --user=debian-sys-maint --host=localhost --password=*** --database=mysql

the hst should be changed but I have no clue where this command is getting from :o
It gets executed from  /etc/mysql/debian-start, but I don't find this command

plz help

---

### Post by reutel on 2006-10-05
fixed; it was executed from /usr/bin/mysql_fix_privilege_tables

---

