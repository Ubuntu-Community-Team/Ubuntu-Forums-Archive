---
title: "mysql-server-5.1 Error 2002 (HY000)"
date: 2011-08-01
forum: Server Platforms
---

### Post by sw00 on 2011-08-01
**Context:**
*Ubuntu 10.04 LTS Server*
*mysql-server-5.1*

**Issue:**
I needed to install mysql-server and migrate/clone the exact same setup as a previous installation on an old server so I followed the Ubuntu Server Guide on setting up MySQL:
```

sudo apt-get install my-sql-server

```

As far as I can tell, the installation was fine and I could login as root user. However upon replacing "my.cnf" with the version from the old server, i get the following error when attempting to connect:
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```
It turns out that "var/run/mysqld/mysqld.sock" doesn't even exist.

Here's my.cnf: [http://pastebin.com/WdyZPWWb]("http://pastebin.com/WdyZPWWb")

There is obviously something in there that's causing problems, however it's running fine on the other server with the exact same config.

---

### Post by Wim Sturkenboom on 2011-08-01
*_ps -ef mysql_* should reveal if the mysql daemon is running; probably not. Not being a Ubuntu server user makes it difficult to tell why; you can try to find the logs; if they exist, they can tell you what went wrong when you started the server.

---

### Post by anuragpatil on 2012-07-18
I messed up with my working MySQL by trying to install multiple instances of MySQL on my Ubuntu and it turned out that none is working. No matter what I did I wasn't able to run a single instance of MySQL also. For over two weeks I struggled to get it working. I searched and searched over internet and read lot of forum posts without success.
 
Let me tell you what worked for me on my Ubuntu 10.04. However, USE THIS AS A LAST RESORT METHOD, YOU WILL LOSE ALL YOUR MYSQL DATA.

<snip>

Hope this helps to someone.

Best Regards.

---

### Post by nothingspecial on 2012-07-18
Old thread.

Closed.

---

