---
title: "MySQL Server not running"
date: 2009-11-06
forum: Server Platforms
---

### Post by dec1211 on 2009-11-06
Been trying to install MySQL Server most of the day and not been able to get it to work. Have Googled a few times and searched here for a few times before deciding to post a thread.

Running Ubuntu Server 9.04

First tried just sudo apt-get install mysql-server and it'd fail saying something regarding mysqld.sock. I ran whereis mysqld.sock and it gave two results, one being /usr/sbin/mysql and the other being /usr/share/man/man1/mysql.1.gz

Tried sudo apt-get autoremove mysql-server and reinstalling multiple times but each time it failed to start.

I've just run apt-get install mysql-server-5.1 and it goes fine, I've entered my root password etc but as soon as it gets past that I get this: 

```
Setting up mysql-server-5.1 (5.1.31-1ubuntu2) ...
 * Stopping MySQL database server mysqld                                 [ OK ]
 * Starting MySQL database server mysqld                                 [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I'm relatively new to linux having just rented a dedicated server.

Any idea guys?

Thanks,
Dec

---

### Post by awclemen on 2009-11-06
This sounds like you are having more problems with apt-get then with MySQL.

I'm running 9.0.4 server on both x86 and 64 bit platform with mysql.  I used 

```
sudo apt-get install mysql-common
```

with no problems.  Maybe try that?

If you can get a hold of the logging, that might contain the error messages that would clear this up.  I believe they are in /var/log/apt in the term.log file.  Can you post the messages that are related to MySQL?

---

### Post by dec1211 on 2009-11-06
```
*@*:~$ sudo apt-get install mysql-common
*snip*
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.1 (5.1.31-1ubuntu2) ...
 * Stopping MySQL database server mysqld                                 [ OK ]
 * Starting MySQL database server mysqld                                 [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Same thing seems to be happening.

Log was rather large so can be found [here]("http://score22.co.uk/uploads/mysqllog.txt").

Thanks

---

### Post by awclemen on 2009-11-06
Maybe I'm going on the wrong tack with this....

The messages say that MySQL is having problems start - so maybe I was wrong to think this is a apt-get problem, you are having problems with MySQL.  Have you checked the mysql logs in /var/log to see if there is anything there?

You might also want to see if you already have mysql running:

```
ps ax | grep mysql
```

Can you post your /etc/mysql/my.cnf as well?

Also seen where an apt-get update and then removal and re-installation have solved the problem:

[https://lists.ubuntu.com/archives/ubuntu-server-bugs/2009-February/010446.html](https://lists.ubuntu.com/archives/ubuntu-server-bugs/2009-February/010446.html)

---

### Post by dec1211 on 2009-11-06
[my.cnf]("http://www.score22.co.uk/uploades/my.cnf")

The log files for mysql in /var/log are all empty, though present.

Checked ps but nothing was running. Will try updating/reinstalling now :)

---

