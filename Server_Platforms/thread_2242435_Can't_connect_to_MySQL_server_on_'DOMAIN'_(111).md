---
title: "Can't connect to MySQL server on 'DOMAIN' (111)"
date: 2014-09-01
forum: Server Platforms
---

### Post by Maheriano on 2014-09-01
I have a default installation of MySQL on my default Ubuntu server, I haven't really changed any settings after install. The default configuration is to disallow external connections to MySQL and I'm trying to allow external connections so I can connect to it from anywhere, mainly so I can use MySQL Workbench instead of PHPMyAdmin. I've made the necessary changes but it still doesn't seem to work.

Here is part of my my.cnf file:

```
[mysqld]
#
# * Basic Settings
#
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
lc-messages-dir = /usr/share/mysql
# skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
# bind-address          = 127.0.0.1
#
# * Fine Tuning
#
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 192K
thread_cache_size       = 8

```

And I logged into my mysql (from localhost) as root to run this:

```
grant all privileges on *.* to 'development'@'%' identified by '**********';
```

Of course I put the correct password in there. Then I ran:

```
flush privileges;
```

I even restarted the MySQL server:

```
sudo service mysql restart
```

However I still cannot connect from my other machine with any user. I can't connect as this user, I can't connect as root, it keeps giving me this 111 error in the title:

```
deemar@Chugger:/etc/mysql$ mysql -u development -p -h domain
Enter password: 
ERROR 2003 (HY000): Can't connect to MySQL server on 'domain' (111)

```

What am I missing to allow external access to MySQL?

---

### Post by sandyd on 2014-09-01
MySQL by default listens only on the localhost (127.0.0.1) interface.

From configuration file above:
```

#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
# bind-address          = 127.0.0.1
```

Uncomment the bind-address line, and bind to 0.0.0.0 to bind to all addresses on the system.

---

### Post by Maheriano on 2014-09-01
> **sandyd said:**
> MySQL by default listens only on the localhost (127.0.0.1) interface.

From configuration file above:
```

#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
# bind-address          = 127.0.0.1
```

Uncomment the bind-address line, and bind to 0.0.0.0 to bind to all addresses on the system.

```
[mysqld]
#
# * Basic Settings
#
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
lc-messages-dir = /usr/share/mysql
# skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 0.0.0.0
#
# * Fine Tuning
#
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 192K
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M

```

```
name@computer:/sbin$ sudo service mysql restart
mysql stop/waiting
mysql start/running, process 6078

```

```
deemar@Chugger:/etc/mysql$ mysql -u development -p -h domain
Enter password: 
ERROR 2003 (HY000): Can't connect to MySQL server on 'domain' (111)

```

Didn't work.

---

### Post by sandyd on 2014-09-01
Whats the output of
```

lsof -Pni :3306
```

---

### Post by Maheriano on 2014-09-01
> **sandyd said:**
> Whats the output of
```

lsof -Pni :3306
```

```
name@computer:~$ lsof -Pni :3306
name@computer:~$
```

---

### Post by sandyd on 2014-09-01
Odd, mysql is refusing to bind to the addresses.

Does /var/log/mysql/error.log have anything that might indicate why it is not binding?

---

### Post by Maheriano on 2014-09-01
> **sandyd said:**
> Odd, mysql is refusing to bind to the addresses.

Does /var/log/mysql/error.log have anything that might indicate why it is not binding?

```
140901 15:40:15 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated an$
140901 15:40:15 [Note] Plugin 'FEDERATED' is disabled.
140901 15:40:15 InnoDB: The InnoDB memory heap is disabled
140901 15:40:15 InnoDB: Mutexes and rw_locks use GCC atomic builtins
140901 15:40:15 InnoDB: Compressed tables use zlib 1.2.8
140901 15:40:15 InnoDB: Using Linux native AIO
140901 15:40:15 InnoDB: Initializing buffer pool, size = 128.0M
140901 15:40:15 InnoDB: Completed initialization of buffer pool
140901 15:40:15 InnoDB: highest supported file format is Barracuda.
140901 15:40:15  InnoDB: Waiting for the background threads to start
140901 15:40:16 InnoDB: 5.5.38 started; log sequence number 364633718
140901 15:40:16 [Note] Server hostname (bind-address): '0.0.0.0'; port: 3306
140901 15:40:16 [Note]   - '0.0.0.0' resolves to '0.0.0.0';
140901 15:40:16 [Note] Server socket created on IP: '0.0.0.0'.
140901 15:40:16 [Note] Event Scheduler: Loaded 0 events
140901 15:40:16 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.5.38-0ubuntu0.14.04.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
140901 17:45:02 [Note] /usr/sbin/mysqld: Normal shutdown

140901 17:45:02 [Note] Event Scheduler: Purging the queue. 0 events
140901 17:45:02  InnoDB: Starting shutdown...
140901 17:45:04  InnoDB: Shutdown completed; log sequence number 364633728
140901 17:45:04 [Note] /usr/sbin/mysqld: Shutdown complete

140901 17:45:04 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated an$
140901 17:45:04 [Note] Plugin 'FEDERATED' is disabled.
140901 17:45:04 InnoDB: The InnoDB memory heap is disabled
140901 17:45:04 InnoDB: Mutexes and rw_locks use GCC atomic builtins
140901 17:45:04 InnoDB: Compressed tables use zlib 1.2.8
140901 17:45:04 InnoDB: Using Linux native AIO
140901 17:45:04 InnoDB: Initializing buffer pool, size = 128.0M
140901 17:45:04 InnoDB: Completed initialization of buffer pool
140901 17:45:04 InnoDB: highest supported file format is Barracuda.
140901 17:45:04  InnoDB: Waiting for the background threads to start
140901 17:45:05 InnoDB: 5.5.38 started; log sequence number 364633728
140901 17:45:05 [Note] Server hostname (bind-address): '0.0.0.0'; port: 3306
140901 17:45:05 [Note]   - '0.0.0.0' resolves to '0.0.0.0';
140901 17:45:05 [Note] Server socket created on IP: '0.0.0.0'.
140901 17:45:05 [Note] Event Scheduler: Loaded 0 events
140901 17:45:05 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.5.38-0ubuntu0.14.04.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)

```

---

### Post by richard51 on 2014-09-02
Error **111** means connection refused, is port **3306** open for the address ranges you wish to allow? Check your firewall* (IpTables, ufw, etc*).

P.S Don't (*try)* to open ports for **0.0.0.0** that is special, just allow the address ranges you want. e.g Allow **192.168.0.0/24** port **3306** for all computers using that local subnet, but leave my.cnf as **0.0.0.0**.

---

### Post by Maheriano on 2014-09-02
Would those things be blocked by default in Ubuntu Server 14.04? I don't even know where to start checking for those things.

---

### Post by richard51 on 2014-09-02
On a fresh install of Ubuntu Server 14.04, **Iptables** will be set to **Allow** for **Input**, **Output** and **Forward**. **UFW** will be disabled, so no, it shouldn't be blocked!

On a side note, I know that you have granted all privileges, but if you have still got **phpMyAdmin** installed, log-in as root on the MySQL machine with **phpMyAdmin**, then check user & database privileges from there. 

You can check **Iptables** and check the status of** UFW** using the following command:
```
$ iptables -L -v --line-numbers
$ ip6tables -L -v --line-numbers
$ ufw status verbose
```

---

### Post by Maheriano on 2014-09-02
> **richard51 said:**
> On a fresh install of Ubuntu Server 14.04, **Iptables** will be set to **Allow** for **Input**, **Output** and **Forward**. **UFW** will be disabled, so no, it shouldn't be blocked!

On a side note, I know that you have granted all privileges, but if you have still got **phpMyAdmin** installed, log-in as root on the MySQL machine with **phpMyAdmin**, then check user & database privileges from there.

You can check **Iptables** and check the status of** UFW** using the following command:
```
$ iptables -L -v --line-numbers
$ ip6tables -L -v --line-numbers
$ ufw status verbose
```

```
name@computer:~$ iptables -L -V --line-numbers
iptables v1.4.21

```

```
name@server:~$ ip6tables -L -V --line-numbers
ip6tables v1.4.21

```

```
name@computer:~$ sudo ufw status verbose
[sudo] password for name: 
WARN: Duplicate profile 'Apache', using last found
WARN: Duplicate profile 'Apache Secure', using last found
WARN: Duplicate profile 'Apache Full', using last found
Status: inactive

```

---

### Post by richard51 on 2014-09-02
**Just a thought:** If 'development' already had privileges set before-hand, I believe you have to  revoke those privileges before setting new ones, otherwise you will have  duplicates.

**Also:** iptables should give more information than that, just try: **sudo iptables -L**

---

### Post by Maheriano on 2014-09-02
> **richard51 said:**
> **Just a thought:** If 'development' already had privileges set before-hand, I believe you have to  revoke those privileges before setting new ones, otherwise you will have  duplicates.

**Also:** iptables should give more information than that, just try: **sudo iptables -L**

```
name@computer:~$ sudo iptables -L -V --line-numbers
[sudo] password for name: 
iptables v1.4.21
name@computer:~$ sudo ip6tables -L -V --line-numbers
ip6tables v1.4.21
name@computer:~$ 

```

EDIT: This worked:

```

name@computer:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

```

---

### Post by volkswagner on 2014-09-02
> **richard51 said:**
> **Just a thought:** If 'development' already had privileges set before-hand, I believe you have to  revoke those privileges before setting new ones, otherwise you will have  duplicates.

**Also:** iptables should give more information than that, just try: **sudo iptables -L**

To check log into mysql as root and run:

```
mysql -u root -p
use mysql;
select User, Host from user;
 
```

---

### Post by Maheriano on 2014-09-02
> **volkswagner said:**
> To check log into mysql as root and run:

```
mysql -u root -p
use mysql;
select User, Host from user;
 
```

development      | %

---

### Post by volkswagner on 2014-09-02
You trimmed a bit from you post on user result.  Was development only listed once?

You may need sudo command for lsof:

```
lsof -Pni :3306
```

Have you tried via ip address rather than host/domain name?  Perhaps there is misdirection via DNS.
Can you ping domain and run host command?  Do you have more than one MySQL server that could be responding?
Can you telnet to port 3306?

```
mysql -u developement -p -h 192.168.x.x
```
```
ping domain
host domain
```
```
telnet domain 3306
```

Are you trying this on your lan, or are you trying this across routers (WAN)?

---

### Post by Maheriano on 2014-09-03
> **volkswagner said:**
> You trimmed a bit from you post on user result.  Was development only listed once?

You may need sudo command for lsof:

```
lsof -Pni :3306
```

Have you tried via ip address rather than host/domain name?  Perhaps there is misdirection via DNS.
Can you ping domain and run host command?  Do you have more than one MySQL server that could be responding?
Can you telnet to port 3306?

```
mysql -u developement -p -h 192.168.x.x
```
```
ping domain
host domain
```
```
telnet domain 3306
```

Are you trying this on your lan, or are you trying this across routers (WAN)?

```
name@computer:~$ sudo lsof -Pni :3306
[sudo] password for name: 
COMMAND  PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
mysqld  1343 mysql   10u  IPv4  16120      0t0  TCP *:3306 (LISTEN)

```

Wait........I'm an idiot! Oh, I'm such a moron, I just realized what I did. I attempted to connect using the IP like you asked, except I used the internal IP (192.168.1.29) and it worked. I found that strange because with the DNS it didn't work. Then I realized my mistake. I forward all port 80 traffic through my switch to that server so people can view the website from the WAN. However, I do not forward port 3306 so the MySQL request is getting lost in my network somewhere. I just forwarded port 3306 to the server and it's working fine now. Sorry to bother you with my nonsense!

---

### Post by volkswagner on 2014-09-03
Glad you sorted it. I don't think most folks assumed you were trying via WAN. it's just a very bad idea
[http://forums.mysql.com/read.php?10,110623,110653](http://forums.mysql.com/read.php?10,110623,110653)

Please mark thread as solved.

---

