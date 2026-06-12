---
title: "MySQL on startup"
date: 2010-06-12
forum: Server Platforms
---

### Post by shmk on 2010-06-12
I have a LAMP on Ubuntu 10.4

The MySQL is binded to a specific IP of a lan.

When the system starts, the MySQL fails to start returning this error
```
[Note] Plugin 'FEDERATED' is disabled.
InnoDB: Started; log sequence number 0 16168543
[ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
[ERROR] Do you already have another mysqld server running on port: 3306 ?
[ERROR] Aborting
```

Then the only sequence of command that make it start is
```
> status mysql
mysql respawn/post-start, (post-start) process PID_OF_MYSQL
> kill PID_OF_MYSQL
> stop mysql
mysql stop/waiting
> start mysql
mysql start/running, process NEW_PID_OF_MYSQL
```

Anyone knows how to solve this problem?

---

### Post by edenCC on 2010-06-12
When mysql starts failed, what's the message from these two commands?

netstat -lnpt | grep 3306

ps -ef | grep mysql

---

### Post by shmk on 2010-06-12
> **edenCC said:**
> When mysql starts failed, what's the message from these two commands?

netstat -lnpt | grep 3306

ps -ef | grep mysql

The netstat returns nothing.

The ps returns "grep mysql", so only itself.

---

### Post by shmk on 2010-06-16
Am I the only one with this kind of problem? :lolflag:

---

