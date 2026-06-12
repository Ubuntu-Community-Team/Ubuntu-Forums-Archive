---
title: "MYSQL error"
date: 2009-10-13
forum: Server Platforms
---

### Post by katana6434 on 2009-10-13
Hi

Hope you can help.

I am running Ubuntu Server 9.04 on a HP server.
I installed mysql 5 using Apt-get.

Whenever I try to connect to mysql i get the following error:

*ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)*

Does anybody know how I can get rid of this error.

Also, when i installed mysql , I didn't get asked about the root password.  What would the default be.  Would it be blank?

also, I'm not exactly a linux expert so you might have to babysit me though some commands. :)
Hope you can help

Thanks

---

### Post by karlson on 2009-10-13
> **katana6434 said:**
> Hi

Hope you can help.

I am running Ubuntu Server 9.04 on a HP server.
I installed mysql 5 using Apt-get.

Whenever I try to connect to mysql i get the following error:

*ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)*

Does anybody know how I can get rid of this error.

Also, when i installed mysql , I didn't get asked about the root password.  What would the default be.  Would it be blank?

also, I'm not exactly a linux expert so you might have to babysit me though some commands. :)
Hope you can help

Thanks

```

ps -fu mysql

```

If nothing is running run:

```

sudo /etc/init.d/mysql restart

```

Output of both would be helpful.

---

### Post by katana6434 on 2009-10-13
Hi Thanks for the reply, output is shown below:

```
ps -fu mysql
```


```
richard@nagios:~$ ps -fu mysql
ERROR: User name does not exist.
```

```
sudo /etc/init.d/mysql restart
```

```
richard@nagios:~$ sudo /etc/init.d/mysql restart
[sudo] password for richard:
sudo: /etc/init.d/mysql: command not found
```

Does this mean that MYSQL is not installed?  The server has Nagios installed, with has a prerequisite of MYSQL.  Nagios is up and running so i assume that MYSQL is up and running?

---

### Post by karlson on 2009-10-13
> **katana6434 said:**
> Hi Thanks for the reply, output is shown below:

```
ps -fu mysql
```


```
richard@nagios:~$ ps -fu mysql
ERROR: User name does not exist.
```

```
sudo /etc/init.d/mysql restart
```

```
richard@nagios:~$ sudo /etc/init.d/mysql restart
[sudo] password for richard:
sudo: /etc/init.d/mysql: command not found
```

Does this mean that MYSQL is not installed?  The server has Nagios installed, with has a prerequisite of MYSQL.  Nagios is up and running so i assume that MYSQL is up and running?

Now for the stupid question:

Do you have mysql-server installed on the machine you're trying to run it?

---

### Post by katana6434 on 2009-10-13
I believe that i have it installed, otherwise Nagios would not be running.

How can i check if it is installed?

---

### Post by katana6434 on 2009-10-13
If I type

mysql --version

i get

```
richard@nagios:~$ mysql --version
mysql  Ver 14.12 Distrib 5.0.75, for debian-linux-gnu (i486) using readline 5.2
```

So it is installed.

---

### Post by wojox on 2009-10-13
Try to start it:

```
sudo /etc/init.d/mysql start
```

---

### Post by karlson on 2009-10-13
> **katana6434 said:**
> If I type

mysql --version

i get

```
richard@nagios:~$ mysql --version
mysql  Ver 14.12 Distrib 5.0.75, for debian-linux-gnu (i486) using readline 5.2
```

So it is installed.

That's a wrong way to check.

```

mysql

```

is a client command.

run 
```

dpkg -l | grep mysql

```

---

### Post by karlson on 2009-10-13
> **wojox said:**
> Try to start it:

```
sudo /etc/init.d/mysql start
```

Please see above.

---

### Post by wojox on 2009-10-13
woops!

---

### Post by katana6434 on 2009-10-15
Thanks for the replies.  Sorry that i couldn't reply yesterday, work was a bit manic.

i have run that command and the output is:

```
richard@nagios:~$ dpkg -l | grep mysql
ii  libdbd-mysql-perl                         4.008-1                           A Perl5 database interface to the MySQL data
ii  libmysqlclient15off                       5.1.30really5.0.75-0ubuntu10.2    MySQL database client library
ii  mysql-client                              5.1.30really5.0.75-0ubuntu10.2    MySQL database client (metapackage depending
ii  mysql-client-5.0                          5.1.30really5.0.75-0ubuntu10.2    MySQL database client binaries
ii  mysql-common                              5.1.30really5.0.75-0ubuntu10.2    MySQL database common files
ii  php5-mysql                                5.2.6.dfsg.1-3ubuntu4.2           MySQL module for php5
```

---

### Post by karlson on 2009-10-15
> **katana6434 said:**
> Thanks for the replies.  Sorry that i couldn't reply yesterday, work was a bit manic.

i have run that command and the output is:

```
richard@nagios:~$ dpkg -l | grep mysql
ii  libdbd-mysql-perl                         4.008-1                           A Perl5 database interface to the MySQL data
ii  libmysqlclient15off                       5.1.30really5.0.75-0ubuntu10.2    MySQL database client library
ii  mysql-client                              5.1.30really5.0.75-0ubuntu10.2    MySQL database client (metapackage depending
ii  mysql-client-5.0                          5.1.30really5.0.75-0ubuntu10.2    MySQL database client binaries
ii  mysql-common                              5.1.30really5.0.75-0ubuntu10.2    MySQL database common files
ii  php5-mysql                                5.2.6.dfsg.1-3ubuntu4.2           MySQL module for php5
```

based on the output mysql-server is not installed, so what are you trying to connect to?

---

### Post by katana6434 on 2009-10-15
OK, so its not installed.  That's confused me now...  Looks like it is just me being stupid then :)

Anyway, so i know for future, what would be listed there if mysql is installed?

Thanks for your help

---

### Post by karlson on 2009-10-15
> **katana6434 said:**
> OK, so its not installed.  That's confused me now...  Looks like it is just me being stupid then :)

Anyway, so i know for future, what would be listed there if mysql is installed?

Thanks for your help

You need mysql-server to be installed on the system if you want to run one locally.  If not the system you will be connecting to needs to have one installed.

---

