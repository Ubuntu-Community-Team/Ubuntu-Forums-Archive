---
title: "MySQL error 2002 (over ssh)"
date: 2010-09-13
forum: Server Platforms
---

### Post by junke1990 on 2010-09-13
Hey guys,

I'm having trouble with MySQL connecting to it over SSH.

I've just installed 10.04.1 LTS today and installed the LAMP package with the SSH in de initial setup.

I am able to connect at the server with mysql -u root -p but not over SSH. I connect to the server by 
```
ssh junke@192.168.254.9 -L3306:localhost:3306
```

The result on my client (my eee) is the following:
```
junke@junke-eee:~$ nmap localhost -p 3306 -A

Starting Nmap 5.35DC1 ( http://nmap.org ) at 2010-09-13 17:55 CEST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00015s latency).
PORT     STATE SERVICE VERSION
3306/tcp open  mysql   MySQL 5.1.41-3ubuntu12.6
| mysql-info: Protocol: 10
| Version: 5.1.41-3ubuntu12.6
| Thread ID: 284
| Some Capabilities: Long Passwords, Connect with DB, Compress, ODBC, Transactions, Secure Connection
| Status: Autocommit
|_Salt: xxxxxxxxxxxxx

```

But if I try to connect with mysqladmin to localhost (from my eee) I get the error 2002 over and over again.

I've tried a lot of things but nothing seems to work.

(all on server side)
adduser junke mysql
chmod -R ug+rwx /var/lib/mysql

changed the sock file from /var/lib/mysql/mysql.sock to /tmp/mysql.sock and I dont know if it has anything to do with it but before and after this change the mysql admin says:

Can't connect to local MySQL server through socket '**/var/run/mysqld/mysqld.sock**' (2) 

Wetter I change this to /tmp/mysql.sock or not. So I checked the .sock file out and it doesn't seems to be there. 

So I checked my my.cnf but as you can see it is stated to /tmp

```
root@ubuntu-server:~# ls -al /tmp
total 8
drwxrwxrwt  2 root root 4096 2010-09-13 18:01 .
drwxr-xr-x 22 root root 4096 2010-09-13 18:01 ..
root@ubuntu-server:~# service mysql restart
mysql start/running, process 5414
root@ubuntu-server:~# cat /etc/mysql/my.cnf |grep socket
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
#socket         = /var/run/mysqld/mysqld.sock
socket          = /tmp/mysqld.sock
#socket         = /var/run/mysqld/mysqld.sock
socket          = /tmp/mysqld.sock
#socket         = /var/run/mysqld/mysqld.sock
socket          = /tmp/mysqld.sock
root@ubuntu-server:~#
```

---

