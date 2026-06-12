---
title: "Mysql fails to start at boot time"
date: 2009-02-24
forum: Server Platforms
---

### Post by God Of Atheism on 2009-02-24
Hi,

When booting, mysqld fails to start. When starting it later on, I manage without problems.

It looks as if mysqld_safe locks the socket, and then tries to start up the `real' mysqld and fails (excerpt from /var/log/daemon.log):
```

Feb 24 15:32:46 servername mysqld_safe[4897]: started
Feb 24 15:32:46 servername mysqld[4901]: 090224 15:32:46  InnoDB: Started; log sequence number 0 43655
Feb 24 15:32:46 servername mysqld[4901]: 090224 15:32:46 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
Feb 24 15:32:46 servername mysqld[4901]: 090224 15:32:46 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 24 15:32:46 servername mysqld[4901]: 090224 15:32:46 [ERROR] Aborting
Feb 24 15:32:46 servername mysqld[4901]: 
Feb 24 15:32:46 servername mysqld[4901]: 090224 15:32:46  InnoDB: Starting shutdown...
Feb 24 15:32:47 servername mysqld[4901]: 090224 15:32:47  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 24 15:32:47 servername mysqld[4901]: 090224 15:32:47 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 24 15:32:47 servername mysqld[4901]: 
Feb 24 15:32:47 servername mysqld_safe[4921]: ended

```

Any idea how to fix this?

Thanks

---

### Post by freerkkalsbeek on 2009-02-24
Don't know how you did it, but it could be that MySQL is started before the networking. If there are no network devices up, it cannot bind to any port....

Check your /etc/rcx.d for the sequence.

Freerk

---

### Post by God Of Atheism on 2009-02-26
> **freerkkalsbeek said:**
> Don't know how you did it, but it could be that MySQL is started before the networking. If there are no network devices up, it cannot bind to any port....

Check your /etc/rcx.d for the sequence.

Freerk

Thanks, I have the following:
```

username@servername:~$ls /etc/rc* | grep -E '(mysql|networking|rc)'
/etc/rc.local
/etc/rc0.d:
K21mysql
K22mysql-ndb
K23mysql-ndb-mgm
S35networking
/etc/rc1.d:
K21mysql
K22mysql-ndb
K23mysql-ndb-mgm
/etc/rc2.d:
S17mysql-ndb-mgm
S18mysql-ndb
S19mysql
S99rc.local
/etc/rc3.d:
S17mysql-ndb-mgm
S18mysql-ndb
S19mysql
S99rc.local
/etc/rc4.d:
S17mysql-ndb-mgm
S18mysql-ndb
S19mysql
S99rc.local
/etc/rc5.d:
S17mysql-ndb-mgm
S18mysql-ndb
S19mysql
S99rc.local
/etc/rc6.d:
K21mysql
K22mysql-ndb
K23mysql-ndb-mgm
S35networking
/etc/rcS.d:
S40networking

```

So, if I understood it right, this means that networking is started before mysql, since the former is in rcS.d.

---

