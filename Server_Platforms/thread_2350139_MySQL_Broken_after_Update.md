---
title: "MySQL Broken after Update"
date: 2017-01-21
forum: Server Platforms
---

### Post by kjaspan on 2017-01-21
A new update containing MySQL showed up today and I installed it. Now MySQL is broken.

I followed the procedure here: **16.04 upgrade broke mysql-server** [http://askubuntu.com/questions/760724/16-04-upgrade-broke-mysql-server](http://askubuntu.com/questions/760724/16-04-upgrade-broke-mysql-server)
 but now I get: 
service mysql start Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl -xe" for details.

root@civet:~# systemctl status mysql.service &#9679; mysql.service - MySQL Community Server Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: en Active: inactive (dead) (Result: exit-code) since Sat 2017-01-21 16:03:52 EST Process: 32687 ExecStartPost=/usr/share/mysql/mysql-systemd-start post (code=e Process: 32686 ExecStart=/usr/sbin/mysqld (code=exited, status=0/SUCCESS) Process: 15576 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exi Main PID: 32686 (code=exited, status=0/SUCCESS)

Jan 21 16:03:52 civet systemd[1]: Failed to start MySQL Community Server. Jan 21 16:03:52 civet systemd[1]: mysql.service: Unit entered failed state. Jan 21 16:03:52 civet systemd[1]: mysql.service: Failed with result 'exit-code'. Jan 21 16:03:52 civet systemd[1]: mysql.service: Service hold-off time over, sch Jan 21 16:03:52 civet systemd[1]: Stopped MySQL Community Server. Jan 21 16:03:52 civet systemd[1]: mysql.service: Start request repeated too quic Jan 21 16:03:52 civet systemd[1]: Failed to start MySQL Community Server. root@civet:~# service mysql stop root@civet:~# service mysql start Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl -xe" for details. root@civet:~# journalctl -xe -- Defined-By: systemd

-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)

-- Unit mysql.service has failed.

-- The result is failed. Jan 21 16:06:09 civet systemd[1]: mysql.service: Unit entered failed state. Jan 21 16:06:09 civet systemd[1]: mysql.service: Failed with result 'exit-code'. Jan 21 16:06:09 civet systemd[1]: mysql.service: Service hold-off time over, sch Jan 21 16:06:09 civet systemd[1]: Stopped MySQL Community Server. -- Subject: Unit mysql.service has finished shutting down -- Defined-By: systemd

-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)

-- Unit mysql.service has finished shutting down. Jan 21 16:06:09 civet systemd[1]: mysql.service: Start request repeated too quic Jan 21 16:06:09 civet systemd[1]: Failed to start MySQL Community Server. -- Subject: Unit mysql.service has failed -- Defined-By: systemd

-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)

-- Unit mysql.service has failed.

-- The result is failed.

Any suggestions? Help would be appreciated.

---

### Post by darkod on 2017-01-21
Hmmm it is very strange a simple update to break mysql. Usually they are thoroughly tested.

So you tried to remove mysql-server package and to install it again? And the apt-get installing shows no errors but mysql doesn't start?

The question you linked from askubuntu is about upgrading the server OS version which broke mysql. In your case you simply applied an update to mysql, right? You are running 16.04 LTS and you weren't performing an upgrade of the whole OS right?

Note, for 16.04 LTS start using 'sudo systemctl start mysql.service' instead of 'sudo service mysql start'. That is the new syntax for systemd. I am using sudo assuming you are not running commands as root like in your example. You don't need sudo as root.

I would also try running something like this to check for any broken dependancies:
```
sudo apt-get update
sudo apt-get install -f
```

---

### Post by raja.genupula on 2017-01-22
Hello,

Execute these commands and provide the output. 

1. Check permissions of MySQL data dir and Database directory

```
**ls -ld /var/lib/mysql/**
```

2. Check in the logs, you can find more information why it's not starting  

```
**less /var/log/mysql/mysqld.log**
```

3. Try checking listening TCP ports while starting 

```
**netstat -ntlp**
```

---

### Post by kjaspan on 2017-01-22
Problem fixed after reinstalling twice. However, MySQL Workbench does not connect. I'm getting the following popup:

[ATTACH=CONFIG]273317[/ATTACH]

mysql is running:

 ps -aef|grep mysql
mysql     1290     1  0 10:00 ?        00:00:02 /usr/sbin/mysqld
kevin     5591  2322  0 10:44 ?        00:00:00 /bin/bash /usr/bin/mysql-workbench
kevin     5592  5591  0 10:44 ?        00:00:00 /bin/sh /usr/bin/catchsegv /usr/lib/mysql-workbench/mysql-workbench-bin
kevin     5594  5592  1 10:44 ?        00:00:01 /usr/lib/mysql-workbench/mysql-workbench-bin

mysql is listening on port 3306:

netstat -an|grep 3306
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     
netstat -an|grep mysql
unix  2      [ ACC ]     STREAM     LISTENING     19224    /var/run/mysqld/mysqld.sock
 
However, if I try to see if root has the rights to connect to mysql, I get:

service mysql stop
root@civet:~#  mysqld_safe --skip-grant-tables &
[1] 5795
root@civet:~# 2017-01-22T15:51:32.663804Z mysqld_safe Logging to syslog.
2017-01-22T15:51:32.668821Z mysqld_safe Logging to '/var/log/mysql/error.log'.
2017-01-22T15:51:32.689453Z mysqld_safe Logging to '/var/log/mysql/error.log'.
2017-01-22T15:51:32.696447Z mysqld_safe Directory '/var/run/mysqld' for UNIX socket file don't exists.

Previously this did work.

Thanks for your help.

---

### Post by darkod on 2017-01-22
Are rights defined for root@127.0.0.1? I think that by default it might work only for root@localhost which is not same. mysql is very specific about that and made to be very secure.

First check if root can connect at all from command line:
```
mysql -u root -p
```

If that works that means mysql root has rights. From Workbench you have to be careful and use correct username@host combination as per the rights you have defined.

---

### Post by kjaspan on 2017-01-22
No, typically I get:
mysql
ERROR 1524 (HY000): Plugin 'mysql_old_password' is not loaded

or

 mysql -uroot
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

---

### Post by raja.genupula on 2017-01-23
Hi , what is the output of 

sudo find / -type s

it will show all the socket files and check for socket file configuration at /etc/my.cnf file. 

Let us know what you are seeing with two actions mentioned above.

---

### Post by kjaspan on 2017-01-23
I solved the problem by doing the following:
[LIST=1]
[*] **Completely remove** mysql. I used:
sudo apt-get purge mysql-server mysql-client mysql-common mysql-server-core-5.5 mysql-client-core-5.5
sudo rm -rf /etc/mysql /var/lib/mysql
 sudo apt-get autoremove 
sudo apt-get autoclean


[*] Reinstall MySQL and Workbench, thus:
apt-get install mysql-server
apt-get install mysql-workbench


[*] Install automysqlbackup
sudo apt-get install automysqlbackup
sudo /usr/sbin/automysqlbackup

sudo rsync -av /etc/ $HOME/etc-backup/
[/LIST]

Thanks for the help.:)

---

### Post by raja.genupula on 2017-01-23
We are glad that you have solved your issue, Please mark this thread as solved. 

Thank you.

---

### Post by kjaspan on 2017-10-28
Once again, got bitten by the snake after upgrading from 17.04 to 17.10.  Getting error when opening Mysql Workbench:

Your connection attempt failed for user 'root' from your host to server at 127.0.0.1:3306:
  Access denied for user 'root'@'localhost'

By repeating the process above - completely uninstalling mysql and reinstalling, the problem went away.

**_[COLOR="#FF0000"]Beware[/COLOR]_**: backup the mysql data directory - in my case /var/lib/mysql - otherwise your databases will be gone! It helps to run regular backups, either via cron or with automysqlbackup.

---

### Post by LHammonds on 2017-10-29
Also, make sure you upgrade your database after the software goes up a version.

```
mysql_upgrade
```

---

### Post by darkod on 2017-10-29
> **kjaspan said:**
> Once again, got bitten by the snake after upgrading from 17.04 to 17.10.  Getting error when opening Mysql Workbench:

In my humble opinion, you are asking for trouble by:
1. Using non-LTS edition.
2. Upgrading each 6 months as new edition gets released.

Linux servers are for stability, not to have the latest and greatest all the time and upgrade each few months. People spend years without upgrading production servers. Even for small home servers use only LTS releases and upgrade to the next LTS only after you have tested your applications and you are sure you can handle that upgrade.

I see the non-LTS releases as "testing phase" for the next LTS, not as something I would use even for nonimportant servers. Their support period of only 9 months shows that. You can install it to test something, but not to upgrade your MySQL server.

It is very easy to issue 'do-release-upgrade' but ubuntu is not designed to be upgraded every 6 months. Even for my desktop at home I use LTS only. And I would definitely not use non-LTS for my home server even though it is only a simple file/media server.

---

### Post by SeijiSensei on 2017-10-29
> **darkod said:**
> People spend years without upgrading production servers.
For example, the server in my home office is running CentOS 5.11 (current version is 7.1).  It handles my mail, a listserver, local DNS, and file storage.  It has been in service for about a decade now and still does what I need.  It's not exposed to the Internet so I'm not worried about security patches.  It just hums along.

---

