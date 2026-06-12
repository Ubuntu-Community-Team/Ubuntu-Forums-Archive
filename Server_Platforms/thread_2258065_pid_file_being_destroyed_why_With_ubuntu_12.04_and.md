---
title: "pid file being destroyed why? With ubuntu 12.04 and postgresql 9.1, pgpoolII-3.3.3"
date: 2014-12-24
forum: Server Platforms
---

### Post by cesar15 on 2014-12-24
Hi, I´ve installed postgresql 9.1 on ubuntu 12.04 with pgpoolII-3.3.3 and pgPoolAdmin

If I try to run pgpool from a terminal with sudo pgpool it seems to start. Viewing ubuntu file explorer I can see how a pgpool.pid file is created at /var/run/pgpool/pgpool.id (this is the path in pgpool.conf)

But after one second the file disappears.

I have tried to change the owner of the directory and the directory permissions but nothing seems to fix it.

If after that I try to stop pgpool wiht sudo pgpool -m fast stop I got an error: Error. pid file not found

It seems like the file is created and suddenly destroyed. I´m wondering why. 

If I try to run pgpool from pgPoolAdmin I got this error: pgpool start failed. pgpool.pid not found.

Like other times, it´s maybe and stupid issue and I´m not being able to solve it as i don´t have a high level of knowledge on those systems.

Any idea about what to try?

Xrry Christmas

---

### Post by cesar15 on 2014-12-26
Maybe is not the pid file being destroyed but that pgpool process starts and is by some reason aborted (and that´s the reason of seeing the file appear and disappear)?

---

### Post by cesar15 on 2015-01-01
Solved. I think the problem was caused by a permission problem. After trying

sudo mkdir /var/run/pgpool
sudo chmod 777 /var/run/pgpool
sudo chown postgres/postgres /var/run/pgpool
sudo postgresql service restart

It seems to be working now.

---

