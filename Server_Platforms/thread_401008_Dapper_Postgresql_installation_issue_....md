---
title: "Dapper: Postgresql installation issue ..."
date: 2007-04-04
forum: Server Platforms
---

### Post by josoaag on 2007-04-04
Hi,

We installed Postgresql 8.1 in our Dapper test server but strangely, the directory /etc/postgresql/main/8.1 is not there.

When we attempt to start the service /etc/init.d/postgresql-8.1 start it just blank.

The only directories found in the system are:
/usr/lib/postgresql 
/usr/include/postgresql 
/usr/share/postgresql

Our system info as follow:
Linux CPU34 2.6.15-28-amd64-generic #1 SMP PREEMPT Thu Feb 1 15:53:41 UTC 2007 x86_64 GNU/Linux

Any help, Thanks!

---

### Post by shufla on 2007-04-24
Hello,

Please try to reinstall this package with apt-get install --reinstall postgresql-8.1 Lists contents of files by using dpkg -L postgresql-8,1 Try to reconfigure package with lowest priority by using dpkg-reconfigure -plow postgresql-8,1

Bye,
Luke

---

