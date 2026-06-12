---
title: "Access Mysql from a remote machine"
date: 2006-09-07
forum: Server Platforms
---

### Post by fredanthony on 2006-09-07
Hi I am trying to use MySQL administrator, GUI, from a remote machine to ease admin of the mysql database, I keep getting a 2003 error and I am unable to connect. Is there something I need to do to allow remote access to the instance of mysql? Thanks.

---

### Post by mentecat on 2006-09-08
Hi,
from /usr/share/doc/mysql-server-5.0/README.Debian

* NETWORKING:
=============
For security reasons, the Debian package has enabled networking only on the
loop-back device using "bind-address" in /etc/mysql/my.cnf.  Check with
"netstat -tlnp" where it is listening. If your connection is aborted
immediately see if "mysqld: all" or similar is in /etc/hosts.allow and read
hosts_access(5).

I think that this is the reason of you problem, but I don't know exactly what you have to change in my.cnf probably the line with "bind-address"

bye

---

### Post by fredanthony on 2006-09-08
Well in my.cnf I changed the bind address from 127.0.0.1 to my local internal IP 192.168.*.*. I then got a different error stating this host is not allowed to connect to the mysql server, I edited the hosts.allow, inserting the internal IP of the remote machine I am connecting from but I still got the same error.

---

### Post by fredanthony on 2006-09-08
Ok i fixed by executing:
> GRANT ALL ON *.* TO 'root'@'192.168.1.%' identified by 'MY_PASSWORD';

---

