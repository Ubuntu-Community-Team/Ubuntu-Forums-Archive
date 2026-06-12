---
title: "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)"
date: 2007-07-18
forum: Server Platforms
---

### Post by burzum on 2007-07-18
I've already searched for solutions and found some, tried them but i can't get it working... :( Im using Ubuntu Server 6.06, just installed it.

The directory exists, the rights are correct. The configfile is correct... I don't have any further ideas. :( It does not start and throws always the same errormessage.

```
root@Wotan:/etc/mysql# aptitude install mysql-server-5.0
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl mysql-client-5.0
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl mysql-client-5.0 mysql-server-5.0
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/28.5MB of archives. After unpacking 65.7MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
send-mail: fatal: open /etc/postfix/main.cf: No such file or directory
Can't send mail: sendmail process failed with error code 1
Selecting previously deselected package libnet-daemon-perl.
(Reading database ... 20515 files and directories currently installed.)
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.38-1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2017-1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.50-1_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_3.0002-2build1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.22-0ubuntu6.06.3_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.22-0ubuntu6.06.3_i386.deb) ...
chage: the shadow password file is not present
Setting up libnet-daemon-perl (0.38-1) ...

Setting up libplrpc-perl (0.2017-1) ...

Setting up libdbi-perl (1.50-1) ...
Setting up libdbd-mysql-perl (3.0002-2build1) ...
Setting up mysql-client-5.0 (5.0.22-0ubuntu6.06.3) ...
Setting up mysql-server-5.0 (5.0.22-0ubuntu6.06.3) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.
.
.
.
.
.
.
.
.
.
.
.
.
.
...failed or took more than 6s.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

root@Wotan:/etc/mysql#

```

---

### Post by aglide on 2007-09-05
I've got the exact same problem.

Did a clean install of 6.06 server, installed apache2, then installed msyql with "apt-get install mysql-server". It installed OK but refuses to start with the mysqld.sock error.

I've scoured the net, but there doesn't seem to be just one solution to this problem.

/etc/mysql/my.cnf has many references to the path to mysqld.sock. They're all the same, and they all point to the path in the error message.

/var/run/mysqld/ is empty, but I was under the impression the daemon creates mysqld.sock on the fly while running. For fun I've created an empty mysqld.sock file and give the mysql user and group ownership/permissions, but it doesn't seem to help.

It smells like a permissions problem to me, but I've tried several different chmod's on /var/run/mysqld/ to no avail.

There's gotta be some simple solution to this, considering it is showing up for more than one of us after a clean install.

---

