---
title: "Mysql only allowing connections from localhost"
date: 2010-05-11
forum: Server Platforms
---

### Post by JigglyWiggly_ on 2010-05-11
Howcome mysql by default is only allowing connections from localhost? I want to access it remotely from another account (not root).

How do I go about doing this?

---

### Post by windependence on 2010-05-11
Edit your my.cnf file. There is a section in there that limits the server to local connections by default.

Should be located at /etc/mysql/my.cnf 

Make sure line skip-networking is commented (or remove line) and add  following line

```
bind-address=YOUR-SERVER-IP
```

Restart the mysql server:

```
# /etc/init.d/mysql restart
```

Grant access to the remote IP address:

```
$ mysql -u root -p mysql
```

You will need to grant access to any existing tables you have:

Let us assume that you are always making connection from remote IP  called 202.54.10.20 for database called webdb for user webadmin,  To   grant access to this IP address type the following command At mysql>  prompt for existing database, enter:
```
mysql> update db set Host='202.54.10.20' where Db='webdb';
mysql> update user set Host='202.54.10.20' where user='webadmin';
```

Type exit command to logout mysql:
```
mysql> exit
```

You will have to open port 3306 on your firewall also.

-Tim

---

