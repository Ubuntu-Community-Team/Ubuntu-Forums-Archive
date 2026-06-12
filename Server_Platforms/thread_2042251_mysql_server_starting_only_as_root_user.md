---
title: "mysql server starting only as root user"
date: 2012-08-14
forum: Server Platforms
---

### Post by satish_j on 2012-08-14
I have recently installed mysql from binary distribution on 12.04 precise into /usr/local/mysql directory.
Everything is running fine except that the mysql service can be started only if i provide 'sudo' to mysqld_safe (i.e as root)
If i use 
```

./bin/mysqld_safe --user=mysql &

```
i get 'permission denied' errors for pid created at /usr/local/mysql/data directory,also for socket file.
This is even though the data directory is owned by mysql user.
Any ideas what can be the problematic condition preventing mysql user to start the service.
Thanks in advance..

---

### Post by satish_j on 2012-08-16
anyone with some hint.

---

### Post by LHammonds on 2012-08-16
I have not seen that problem before.  I am guessing it is due to how it was installed.  

Not sure if it would help you solve anything but you can look thru my notes on how I install a MySQL server in my sig.

LHammonds

---

### Post by koenn on 2012-08-16
hm yeah, it doen't look like a regular install from repos, judging by the paths, so there's possibly bits and pieces missing here and there

I still  think it's a permission problem, possibly write access to dirs such as /var/run or /var/lock, 

satish, are you sure mysql is trying to create a pid file in  /usr/local/mysql/data  ?

and whu didn't you just install the versopn from the repos ?

---

### Post by satish_j on 2012-08-17
> **koenn said:**
> hm yeah, it doen't look like a regular install from repos, judging by the paths, so there's possibly bits and pieces missing here and there

I still  think it's a permission problem, possibly write access to dirs such as /var/run or /var/lock, 

satish, are you sure mysql is trying to create a pid file in  /usr/local/mysql/data  ?

and whu didn't you just install the versopn from the repos ?

Iam interested in the binary distribution and not in the packages available from software manager.
I did followed the instructions as directed,along with proper permissions to the directories,but still am facing the problem.
I know that there is a file created in /tmp directory as /tmp/mysql.sock,but have no idea about the pid file you are talking about.
The data directory inside /usr/local/mysql is owned by mysql user,so even if the pid file is created at this path,there should not be permission problem as user 'mysql' has access to that directory.

---

