---
title: "Unable to upgrade MySQL server - Access denied for user 'debian-sys-maint'"
date: 2017-04-13
forum: Server Platforms
---

### Post by mbnoimi on 2017-04-13
Hi,

Recently I upgraded my server as shown below but unfortunately MySQL server couldn't upgrade :(

How can I fix this issue?

```
# apt-get update && apt-get -y upgrade && apt-get -y autoremove
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [512 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [500 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [456 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [442 kB]
Fetched 2,216 kB in 1s (1,137 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  update-notifier-common
The following packages will be upgraded:
  dnsmasq-base
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 295 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 dnsmasq-base amd64 2.75-1ubuntu0.16.04.2 [295 kB]
Fetched 295 kB in 0s (298 kB/s)
(Reading database ... 123077 files and directories currently installed.)
Preparing to unpack .../basmahanese_2.75-1ubuntu0.16.04.2_amd64.deb ...
Unpacking dnsmasq-base (2.75-1ubuntu0.16.04.2) over (2.75-1ubuntu0.16.04.1) ...
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Setting up mysql-server-5.7 (5.7.17-0ubuntu0.16.04.2) ...
mysql_upgrade: Got error: 1045: Access denied for user 'debian-sys-maint'@'localhost' (using password: YES) while connecting to the MySQL server
Upgrade process encountered error and will not continue.
mysql_upgrade failed with exit status 11
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.
dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Setting up dnsmasq-base (2.75-1ubuntu0.16.04.2) ...
Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by mbnoimi on 2017-04-13
I tried to execute the following query
```
GRANT ALL PRIVILEGES ON *.* TO &#8216;debian-sys-maint&#8217;@'localhost&#8217; IDENTIFIED BY &#8216;pasw&#8217; WITH GRANT OPTION;
```

Where I took pasw from /etc/mysql/debian.cnf but it give m

```
Failed to execute SQL : SQL GRANT ALL PRIVILEGES ON *.* TO &#8216;debian-sys-maint&#8217;@'localhost&#8217; IDENTIFIED BY &#8216;pasw&#8217; WITH GRANT OPTION; failed : You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '-sys-maint&#8217;@'localhost&#8217; IDENTIFIED BY &#8216;pasw&#8217; WITH GRANT OPTI' at line 1
```

**IMPORTANT**: I don't face any problem with MySQL server except upgrade issue. I can access using root user without any problem

---

### Post by darkod on 2017-04-13
Don't try that, you should be doing this with adding privileges inside mysql. The messages clearly say the package was left unconfigured previously...

How about if you try to configure it now? This can also fail if you have no free space left. Post the output of:
```
df -h
sudo dpkg --configure mysql-server-5.7
```

Note: I am using sudo in the command because i assume you will be running this as your own admin user, not as root.

---

### Post by mbnoimi on 2017-04-13
When I run the following I got nothing 

```
SELECT User FROM mysql.user WHERE user='debian-sys-maint';
```

---

### Post by mbnoimi on 2017-04-13
> **darkod said:**
> Don't try that, you should be doing this with adding privileges inside mysql. The messages clearly say the package was left unconfigured previously...

How about if you try to configure it now? This can also fail if you have no free space left. Post the output of:
```
df -h
sudo dpkg --configure mysql-server-5.7
```

Note: I am using sudo in the command because i assume you will be running this as your own admin user, not as root.

The result:

```
root@cpp-tech:~# df -h
Filesystem                    Size  Used Avail Use% Mounted on
udev                          7.9G     0  7.9G   0% /dev
tmpfs                         1.6G   17M  1.6G   2% /run
/dev/mapper/cppSync--vg-root  534G   42G  465G   9% /
tmpfs                         7.9G     0  7.9G   0% /dev/shm
tmpfs                         5.0M     0  5.0M   0% /run/lock
tmpfs                         7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda1                     472M  105M  344M  24% /boot
tmpfs                         1.6G     0  1.6G   0% /run/user/0
root@cpp-tech:~# dpkg --configure mysql-server-5.7
Setting up mysql-server-5.7 (5.7.17-0ubuntu0.16.04.2) ...
mysql_upgrade: Got error: 1045: Access denied for user 'debian-sys-maint'@'localhost' (using password: YES) while connecting to the MySQL server
Upgrade process encountered error and will not continue.
mysql_upgrade failed with exit status 11
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.7
root@cpp-tech:~#
```

There is an enough disk free

---

### Post by darkod on 2017-04-13
You can also try the following for any hald-upgraded packages:
```
sudo apt-get install -f
```

If it still doesn't work, check some solutions on google for that debian-sys-maint message, but it looks weird to me to have to touch inside mysql for this. Package installation and control should not be related to users inside mysql...

---

### Post by mbnoimi on 2017-04-13
> **darkod said:**
> You can also try the following for any hald-upgraded packages:
```
sudo apt-get install -f
```

If it still doesn't work, check some solutions on google for that debian-sys-maint message, but it looks weird to me to have to touch inside mysql for this. Package installation and control should not be related to users inside mysql...

Actually I googled a lot before posting this thread but unfortunately I got nothing about this issue :( 

Any way, I triied your suggestion before and I get this result:
```
# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mysql-server-5.7 (5.7.17-0ubuntu0.16.04.2) ...
mysql_upgrade: Got error: 1045: Access denied for user 'debian-sys-maint'@'localhost' (using password: YES) while connecting to the MySQL server
Upgrade process encountered error and will not continue.
mysql_upgrade failed with exit status 11
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.
dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by mbnoimi on 2017-04-13
The nearest result I got is the following but it didn't work for my problem
[https://mirzmaster.wordpress.com/2009/01/16/mysql-access-denied-for-user-debian-sys-maintlocalhost/](https://mirzmaster.wordpress.com/2009/01/16/mysql-access-denied-for-user-debian-sys-maintlocalhost/)

---

### Post by mbnoimi on 2017-04-24
May I get some help guys? This annoying issue still occurs :(

---

