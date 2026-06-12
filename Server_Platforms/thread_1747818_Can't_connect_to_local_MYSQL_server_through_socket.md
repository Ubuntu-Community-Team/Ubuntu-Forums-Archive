---
title: "Can't connect to local MYSQL server through socket '/tmp/mysql.sock' (2)"
date: 2011-05-03
forum: Server Platforms
---

### Post by thoufiq on 2011-05-03
Hello All,
           When i am trying to upgrade from mysql5.1 to mysql5.5, i got a errors like this

[COLOR=Red][B]root@dhcppc4:~# mysql_upgrade
Looking for 'mysql' as: mysql
Looking for 'mysqlcheck' as: mysqlcheck
Running 'mysqlcheck' with connection arguments: '--port=3306' '--socket=/tmp/mysql.sock'
mysqlcheck: Got error:2002:Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2) when trying to connect
FATAL ERROR: Upgrade failed[/B][/COLOR]

Also, when i am trying to stop and start the mysql server, it tells that [COLOR=Red]**dhcppc4.pid**[/COLOR]  file is not found.

Pls, anyone help me to overcome from this error.

Thanks a lot.

---

### Post by falko on 2011-05-03
Does /tmp/mysql.sock exist? What are the permissions of the /tmp directory? Also check that the partition that contains /tmp isn't full.

---

### Post by thoufiq on 2011-05-03
> **falko said:**
> Does /tmp/mysql.sock exist? What are the permissions of the /tmp directory? Also check that the partition that contains /tmp isn't full.


Hello Falko,
                   /tmp/ doesn't have mysql.sock and also when i am giving the command ls -l, it shows total 0. Is any file is missing in /tmp/.

[B][COLOR=Red]root@dhcppc4:/tmp# ls -l
total 0[/COLOR][/B]

Help me...

---

