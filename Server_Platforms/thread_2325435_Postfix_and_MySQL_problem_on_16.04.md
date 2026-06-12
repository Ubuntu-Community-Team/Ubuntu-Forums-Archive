---
title: "Postfix and MySQL problem on 16.04"
date: 2016-05-22
forum: Server Platforms
---

### Post by mleisher on 2016-05-22
[LIST=1]
[*]Installed postfix, postfix-mysql, and mariadb-server.
[*]Configured with alias_map=mysql:/etc/postfix/aliases.cf.
[*]postconf -q alias mysql:/etc/postfix/aliases.cf expands aliases correctly.
[*]postfix responds with "Temporary lookup failure" for every single address, alias or not.
[/LIST]

/usr/sbin/postconf loads /usr/lib/postfix/postfix-mysql.so.1.0.1 on demand, /usr/lib/postfix/sbin/master does not.

---

### Post by mleisher on 2016-05-22
After further investigation, there's an error connection to the local socket. I changed permissions on /var/run/mysqld/ to be world readable/writable. Still had the same problem. However when connecting to 127.0.0.1:3306, all works properly.

---

