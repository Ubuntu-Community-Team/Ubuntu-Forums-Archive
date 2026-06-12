---
title: "mysql 32 bit multithread on lucid"
date: 2010-06-18
forum: Server Platforms
---

### Post by chrone on 2010-06-18
dear all,

sorry about this noob question, but does ubuntu 10.04 support multithread on mysql 32 bit?

/chrone

---

### Post by sjinks on 2010-06-19
It does. MySQL uses threaded model, not prefork. Every connection is handled by the new thread (see options with "thread" in [this page]("http://dev.mysql.com/doc/refman/5.0/en/mysqld-option-tables.html"))

---

### Post by chrone on 2010-06-19
> **sjinks said:**
> It does. MySQL uses threaded model, not prefork. Every connection is handled by the new thread (see options with "thread" in [this page]("http://dev.mysql.com/doc/refman/5.0/en/mysqld-option-tables.html"))

thanks, i really appreciate it. :)

i have been told by my friend that only the 64bit mysql was configured to use multithread by default. that's why i just want to reconfirm this.

thanks for the info. i guess only innodb was multithreaded properly. unfortunately, in my office, the database mostly use myisam database. or perhaps, my programmer didn't create the database efficiently with threads, that's why the mysql always running with single thread only. it only uses one core all the time though i had dual-core processors.

---

### Post by sjinks on 2010-06-20
MySQL runs one process but multiple threads. You can check this yourself by putting mysql under load and issuing this command:

ps -C mysqld -othcount

It will display the number of threads MySQL is running.

---

### Post by chrone on 2010-06-21
> **sjinks said:**
> MySQL runs one process but multiple threads. You can check this yourself by putting mysql under load and issuing this command:

ps -C mysqld -othcount

It will display the number of threads MySQL is running.

> ps -C mysqld -othcount
THCNT
  759

that's weird, the dual core processor only show 1 core active with mysql though. :(

---

### Post by chrone on 2010-06-21
or is it possible to see how many concurrent thread is processed right now by the mysql server?

---

### Post by sjinks on 2010-06-21
MySQL supports multiple cores [only since 5.4]("http://dev.mysql.com/doc/refman/5.4/en/mysql-nutshell.html").

---

### Post by sjinks on 2010-06-21
> **chrone said:**
> or is it possible to see how many concurrent thread is processed right now by the mysql server?

sudo mysqladmin --defaults-extra-file=/etc/mysql/debian.cnf status | awk '{ print $4 }'

---

### Post by chrone on 2010-06-21
> **sjinks said:**
> MySQL supports multiple cores [only since 5.4]("http://dev.mysql.com/doc/refman/5.4/en/mysql-nutshell.html").

oic, that's why. it seems that only innodb has this advantage. and i'm afraid that mysql 5.4 is not supported at this current long term support of ubuntu, perhaps the next one, 12.04. :(

thanks for the information. i really appreciate it.

> **sjinks said:**
> sudo mysqladmin --defaults-extra-file=/etc/mysql/debian.cnf status | awk '{ print $4 }'

thanks for the tips, i'll give it a try tomorrow at the office.

---

