---
title: "trouble connecting application to database server?"
date: 2011-08-19
forum: Server Platforms
---

### Post by 007casper on 2011-08-19
I ping the ips from one server to other.  It seems fine from each server.
4 packets transmitted, 4 received, 0% packet loss, time 3000ms

however, the application cant connect to the database server.
I tried to connect from the app server...> 
mysql -u user -h 192.168.1.3 -p databasename
ERROR 1130 (HY000):Host 'app.domain.com' is not allowed to connect to this MySQL server

I also tried with root> 
mysql -u root -h 192.168.1.3 -p
ERROR 1130 (HY000):Host 'app.domain.com' is not allowed to connect to this MySQL server

?

---

### Post by tcsmith1978 on 2011-08-19
Sounds like you need to grant access to that user from that host. Try logging in as root and checking what user and hosts u have set up. Let me know if u need help doing this.

---

### Post by SeijiSensei on 2011-08-19
MySQL uses 'user'@'hostname' to define permissions.  By default 'root'@'localhost' has full permissions.  But if you try connecting from a remote machine as root, you'll be blocked.

I use PostgreSQL where access controls are less obtuse than those in MySQL.  If you're sticking with MySQL, you need to start by reading [this document](http://dev.mysql.com/doc/refman/5.1/en/privilege-system.html).

---

### Post by 007casper on 2011-08-19
@ SeijiSensei - thank you for the link, it is a great reference.  I really appreciate it.  I am reading it.  It seems as it is explaining why I am having this problem.  However, I couldnt find a solution on that page.  Maybe the information I am looking for looking at me on the face somewhere in there. I am going through rest of the links.

@ tcsmith1978 - I logged in from the database server...

on the database server......
was able to login to database server```

user@data:~$ mysql -u root -p
mysql> SELECT User, Host, Password FROM mysql.user;
+------------------+-----------+-------------------------------------------+
| User             | Host      | Password                                  |
+------------------+-----------+-------------------------------------------+
| root             | localhost | *cccccccccccccccccccccccccccccccccccccccc |
| debian-sys-maint | localhost | *cccccccccccccccccccccccccccccccccccccccc |
| appuser          | appserver | *cccccccccccccccccccccccccccccccccccccccc |
+------------------+-----------+-------------------------------------------+
```
```

mysql> SHOW GRANTS FOR 'appuser'@'appserver';
+----------------------------------------------------------------------------------------------------------------+
| Grants for appuser                                                                                   |
+----------------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'appuser'@'appserver' IDENTIFIED BY PASSWORD '*3333333333333333333333333333333333333333' |
| GRANT ALL PRIVILEGES ON `databasename`.* TO 'appuser'@'appserver'                                          |
+----------------------------------------------------------------------------------------------------------------+

mysql>quit
```

cant login as a appuser
```

user@data:~$ mysql -u appuser -p
ERROR 1045 (28000): Access denied for user 'appuser'@'localhost' (using password: YES)
```

however, I set appuser@appserver not on localhost.

---

### Post by tcsmith1978 on 2011-08-20
Because you're logging in on the server you need to grant access to 'appuser'@'localhost' rather than 'appuser'@'appserver'. There is no user 'appuser'@'localhost'

---

### Post by 007casper on 2011-08-20
[http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html](http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html)

I followed that link.  

192.168.1.172  app.server.com 

It works now.  I just put the internal IP as a Host. Then, tested from application server and connected to the database server without a problem.  Should I also grant 'appuser'@'localhost' on database server?

```
+------------------+-----------+---------------------------------------------------+
| User             | Host      | Password                                          |
+------------------+-----------+---------------------------------------------------+
| root             | localhost         | *2AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAB |
| root             | mysql             | *2AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAB |
| root             | 127.0.0.1         | *2AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAB |
| debian-sys-maint | localhost         | *2AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAB |
| appuser          | 192.168.1.172     | *2AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAB |
+------------------+-----------+---------------------------------------------------+ 
```

I have couple things missing on /etc/mysql/my.cnf, such as 'pid-file', and the other 'skip-networking'
pid-file        = /var/run/mysqld/mysqld.pid

I would like to add it... but what does it do?

---

### Post by bbqroast on 2011-08-21
Can I just point out that if this app is downloaded it would be possible for it to be reverse compiled and your db username/password to be worked out.

---

### Post by 007casper on 2011-08-22
so you are suggesting that I use localhost, and appserver on the database server, instead of lan ip of the appserver.  It wasnt resolving when I used a hostnames such as appserver, and mysql-server.  I put the lan ip of the application server on mysql, and went to the application server and put the database server lan ip.  It worked.  

you are thinking this is better because they might not able to locate server through hostname
+------------------+-----------+---------------------------------------------------+
| appuser          | appserver | *cccccccccccccccccccccccccccccccccccccccc |
+------------------+-----------+---------------------------------------------------+

---

### Post by Sanados on 2011-08-22
When you are connecting to mysql on localhost it is (in most cases) better to connect to localhost and not to ip.
When using localhost you can connect to your database via mysql.socket which should be 20% faster than over ip.

skip-networking is an old option which should not be present in current versions.
(was replaced by bind-address)
When you connect to localhost over sockets you have no need for the mysql server to listen on any port.

---

### Post by 007casper on 2011-08-22
originally I had /etc/hosts on both servers.  Database server, and application server.  Database server only has mysql, and nothing else.  However, application server has mysql but I am not using it.

on app server /etc/hosts
```

127.0.0.1 localhost
157.166.225.26 appserver.example.com appserver
192.168.1.3 mysql.example.com mysql
192.168.1.172 appserver.example.com appserver

```

then on database server  /etc/hosts
```

127.0.0.1 localhost
157.166.101.4 mysql.example.com mysql
192.168.1.3 mysql.example.com mysql
192.168.1.172 appserver.example.com appserver

```

then on database server /etc/mysql/my.cnf
```

bind-address = mysql
```

then, on mysql I had 
```

user@mysql:~$ mysql -u root -p
mysql> SELECT User, Host, Password FROM mysql.user;
+------------------+-----------+-------------------------------------------+
| User             | Host      | Password                                  |
+------------------+-----------+-------------------------------------------+
| root             | localhost | *cccccccccccccccccccccccccccccccccccccccc |
| debian-sys-maint | localhost | *cccccccccccccccccccccccccccccccccccccccc |
| appuser          | appserver | *cccccccccccccccccccccccccccccccccccccccc |
+------------------+-----------+-------------------------------------------+
```

I couldnt make it work.  I think maybe my real issue was database access.

on the appserver, on the config file I put 
```

db_host: 'mysql'
```

I even tried
```
db_host: 'mysql.example.com'
```

Since, I couldnt make it work.  I changed the host to lan IP
/etc/mysql/my.cnf
```

bind-address = 192.168.1.3
```
```

+------------------+-----------+-------------------------------------------+
| appuser          | 192.168.1.172     | *2AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAB |
+------------------+-----------+-------------------------------------------+

```

Maybe I should've done 
```

+------------------+-----------+---------------------------------------------------+
| appuser | localhost | *cccccccccccccccccccccccccccccccccccccccc |
+------------------+-----------+---------------------------------------------------+

```

then give proper permissions.  

Somehow, I figured the application server wouldnt communicate with database server.  I figured when you do localhost, it only looks for internal communication, and wont step out to lan.

I was surprised on the pull internally, from database server to application server.  The ratio is crazy.  It pulls around 5mb to 2mb from database server, and pumps around 1mb outgoing to public ip.

So, I am going to try

on the database server
/etc/mysql/my.cnf
```
bind-address = mysql
```

then mysql
```

+------------------+-----------+---------------------------------------------------+
| appuser | localhost | *cccccccccccccccccccccccccccccccccccccccc |
+------------------+-----------+---------------------------------------------------+

```

then, I will try to connect to database server from the appserver.
mysql -u user -h localhost -p databasename

and on the appserver on the config file I put 
db_host: 'localhost'

does that look ok?

---

### Post by Sanados on 2011-08-23
i would use the ip adress of the server as bind-address and not a hostname. (not searched the manual but i think mysql does not like hostnames as address)

When mysql starts up correct and binds on the ip.
(netstat -ln|grep mysql or just try to telent to that ip on that port)

you can connect to that mysql server by using "mysql" as hostname ... as the name ist translated to an ip address anyway and the incoming connection to mysql will be assigned to the ip.

also enter ip of the server that has access to mysql
(or just use the net the 192.168.1.0/24 (192.168.1.%) as host)

---

