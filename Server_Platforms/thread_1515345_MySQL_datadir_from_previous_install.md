---
title: "MySQL datadir from previous install"
date: 2010-06-22
forum: Server Platforms
---

### Post by mwjones on 2010-06-22
I was running Ubuntu 9.10 and had the MySQL datadir moved to a different directory, **/store/mysql**.  Due to a filesystem problem on the upgrade to Ubuntu 10.04, I was forced to reinstall.  My /store/mysql was copied back over, and I made the appropriate changes to **/etc/mysql/my.cnf** and **/etc/apparmor.d/usr.sbin.mysqld**, but MySQL hangs when I go to start it and nothing is showing up in any of the logs.  

How do I get MySQL to recognize the datadir from the previous install?

---

### Post by Ryan Dwyer on 2010-06-22
Are all the files in /store/mysql owned by mysql (and /store/mysql itself)?

---

### Post by mwjones on 2010-06-22
> **Ryan Dwyer said:**
> Are all the files in /store/mysql owned by mysql (and /store/mysql itself)?

Correct, everything starting at **/store/mysql** and under it are mysql:mysql on ownership.  The modes of the files match those of the files in **/var/lib/mysql**.

I also had both reloaded and restarted apparmor after modifying **/etc/apparmor.d/usr.sbin.mysqld**.

---

### Post by Ryan Dwyer on 2010-06-22
Did you restore the "mysql" database from your backup? If you did, something might not be right with it. Try replacing it with the one from /var/lib/mysql.

If you still have no luck, try reverting the config back to /var/lib/mysql just to see if it starts properly.

---

### Post by mwjones on 2010-06-22
> **Ryan Dwyer said:**
> Did you restore the "mysql" database from your backup? If you did, something might not be right with it. Try replacing it with the one from /var/lib/mysql.

If you still have no luck, try reverting the config back to /var/lib/mysql just to see if it starts properly.

Reverted the config.  Right now, mysql is not running:

```
$ ps -ef | grep -i mysql
mwjones    22465 18758  0 09:26 pts/3    00:00:00 grep --color=auto -i mysql
```

But when I tell it to start:

```
$ sudo service mysql start
start: Job is already running: mysql
```

Which led me to searching for that message, and I found this bug:  [https://bugs.launchpad.net/null/+bug/551097](https://bugs.launchpad.net/null/+bug/551097)

The last reply is: > the short answer: you have to run mysqld as user mysql

So I ran: ```
sudo -u mysql /usr/sbin/mysqld &
```

This allowed me to connect and authenticate using **/var/lib/mysql**.  At this point, I:

[LIST=1]
[*]Issued **sudo service mysql stop**
[*]Changed the MySQL and apparmor configs back to use **/store/mysql**
[*]Restarted apparmor
[*]Issued **sudo service mysql start**
[/LIST]

Now everything works!  My guess is that there was some sort of mutex that was holding up everything, and running the mysqld manually sorted it all out.  Thanks for the help, Ryan!

---

