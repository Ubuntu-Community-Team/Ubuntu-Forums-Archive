---
title: "my mySQL server can't work. Please Advice ..."
date: 2007-06-07
forum: Server Platforms
---

### Post by syahrizal on 2007-06-07
I want to use the mySQL server for testing my PHP homework. But the server can't be started.
Then this message below was appeared in the terminal:
"
root@my-computer:~# mysqld
070607  9:35:53  InnoDB: Started; log sequence number 0 43655
070607  9:35:53 [ERROR] Can't start server : Bind on unix socket: No such file or directory
070607  9:35:53 [ERROR] Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
070607  9:35:53 [ERROR] Aborting

070607  9:35:53  InnoDB: Starting shutdown...
070607  9:35:55  InnoDB: Shutdown completed; log sequence number 0 43655
070607  9:35:55 [Note] mysqld: Shutdown complete
"

The mySQL program's was all installed properly.
(server, client, module for PHP5 - all version 5.0.22ubuntu6.06)
But, /var/run/mysqld directory doesn't exist.

Please give some advice.

Thank you.

Yours regardly,

syahrizal

---

### Post by turinglabs on 2007-06-08
This should do the trick:

sudo mkdir /var/run/mysqld
sudo chmod 755 /var/run/mysqld
sudo chown mysql.root /var/run/mysqld

You should start MySQL with /etc/init.d/mysql start

---

