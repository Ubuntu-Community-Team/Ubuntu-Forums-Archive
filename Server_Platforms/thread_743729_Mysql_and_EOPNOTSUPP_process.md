---
title: "Mysql and EOPNOTSUPP process"
date: 2008-04-02
forum: Server Platforms
---

### Post by dannet on 2008-04-02
Hello, I have a constant mysql process using 10-20% CPU, its very strange because the process is always present, if I restart apache and mysql and I just open the phpmyadmin or any website connecting to the DB I get this error. 

With strace I have seen tha tthe process details are:

```
futex(0x87326c4, 0x5 /* FUTEX_??? */, 1) = 1
futex(0x8732174, FUTEX_WAKE, 1)         = 1
select(15, [13 14], NULL, NULL, NULL)   = 1 (in [14])
fcntl64(14, F_SETFL, O_RDWR|O_NONBLOCK) = 0
accept(14, {sa_family=AF_FILE, path="&#1279;"}, [2]) = 25
fcntl64(14, F_SETFL, O_RDWR)            = 0
getsockname(25, {sa_family=AF_FILE, path="/var/run/mysql"}, [30]) = 0
fcntl64(25, F_SETFL, O_RDONLY)          = 0
fcntl64(25, F_GETFL)                    = 0x2 (flags O_RDWR)
fcntl64(25, F_SETFL, O_RDWR|O_NONBLOCK) = 0
setsockopt(25, SOL_IP, IP_TOS, [8], 4)  = -1 EOPNOTSUPP (Operation not supported)
```

The strace show that this piece of code is being repeated everytime that any website or app is using the database.

Server specs:
Core2Duo E6750
PHP Version 5.2.5
MySQL 5.0.45

Anyone know how to solve it?

Thanks in advance

**EDIT: **I have seen that the process call to the path /var/run/mysql in:

```
getsockname(15, {sa_family=AF_FILE, path="/var/run/mysql "}, [30]) = 0
```

but in my system the path doesnt exists, its /var/run/mysqld/ and I cant find a call to "/var/run/mysql" in any file of the server.

---

