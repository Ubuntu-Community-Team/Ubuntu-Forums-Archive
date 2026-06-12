---
title: "Starting MySQL database server failed"
date: 2015-01-10
forum: Server Platforms
---

### Post by iacoposk8 on 2015-01-10
Hello everyone, I have this problem:

```

sudo /etc/init.d/mysql start
[FAIL] Starting MySQL database server: mysqld . . . . . . . . . . . . . . failed!

```
this morning, the same command worked.

in /var/log I checked all the files that begin with "mysql", but they are all empty.
how to solve? thanks

---

### Post by Vegan on 2015-01-10
does it work ok on a reboot, could be one of a few problems

---

### Post by iacoposk8 on 2015-01-10
Also reboot causes the same problem

---

### Post by steeldriver on 2015-01-10
How and where did you install the mysql-server?

FYI I think the recommended way to start it on Ubuntu is still via the `service`  commands rather than by calling the initscript directly

```

sudo service mysql start

```

---

### Post by iacoposk8 on 2015-01-11
I used this command to install apache and mysql.
```
sudo apt-get install apache2-mpm-prefork mysql-server libapache2-mod-php5 php5-mysql php5-gd phpmyadmin
```
 the command you suggested me always the same problem

---

### Post by Doug S on 2015-01-11
> **iacoposk8 said:**
> in /var/log I checked all the files that begin with "mysql", but they are all empty.Yes, but did you check for "mysql" within other log files? Example:```
doug@s15:~/sguide-1204$ [COLOR=#ff0000]grep mysqld /var/log/kern.log.1[/COLOR]
Dec 29 15:54:45 s15 kernel: [   27.394492] type=1400 audit(1419897285.029:19): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/mysqld" pid=1381 comm="apparmor_parser"
Dec 29 15:57:51 s15 kernel: [   27.306096] audit: type=1400 audit(1419897471.096:20): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=1443 comm="apparmor_parser"
Jan  4 20:55:05 s15 kernel: [   27.289819] audit: type=1400 audit(1420433705.073:24): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=1436 comm="apparmor_parser"
Jan  5 00:03:06 s15 kernel: [   27.647628] audit: type=1400 audit(1420444986.432:27): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=1442 comm="apparmor_parser"
```

---

### Post by iacoposk8 on 2015-01-11
```
Jan  9 22:50:30 raspberrypi kernel: [ 3236.860596] [ 2096]     0  2096      440       95       4       24             0 mysqld_safe
Jan  9 22:50:30 raspberrypi kernel: [ 3236.860639] [ 2487]   107  2487    87292     6013      62     6713             0 mysqld
Jan  9 22:50:31 raspberrypi kernel: [ 3236.894470] Out of memory: Kill process 2487 (mysqld) score 93 or sacrifice child
Jan  9 22:50:31 raspberrypi kernel: [ 3236.894554] Killed process 2487 (mysqld) total-vm:349168kB, anon-rss:22968kB, file-rss:1084kB
Jan  9 23:29:13 raspberrypi kernel: [ 5559.704433] [ 2096]     0  2096      440       23       4        4             0 mysqld_safe
Jan  9 23:29:13 raspberrypi kernel: [ 5559.710374] [ 3901]   107  3901    88551    10290      59        0             0 mysqld
Jan  9 23:29:13 raspberrypi kernel: [ 5559.727285] Out of memory: Kill process 3901 (mysqld) score 75 or sacrifice child
Jan  9 23:29:13 raspberrypi kernel: [ 5559.727341] Killed process 3901 (mysqld) total-vm:354204kB, anon-rss:40608kB, file-rss:572kB
Jan  9 23:48:05 raspberrypi kernel: [ 6692.111355] [ 2096]     0  2096      440       22       4        4             0 mysqld_safe
Jan  9 23:48:05 raspberrypi kernel: [ 6692.125169] [ 4856]   107  4856    84386     9332      52        0             0 mysqld
Jan  9 23:48:05 raspberrypi kernel: [ 6692.127857] Out of memory: Kill process 4856 (mysqld) score 68 or sacrifice child
Jan  9 23:48:05 raspberrypi kernel: [ 6692.127890] Killed process 4856 (mysqld) total-vm:337544kB, anon-rss:37240kB, file-rss:88kB
Jan  9 23:48:05 raspberrypi kernel: [ 6692.342084] [ 2096]     0  2096      440       22       4        4             0 mysqld_safe
Jan 10 08:57:27 raspberrypi kernel: [ 3307.355212] [ 2112]     0  2112      440       95       4       24             0 mysqld_safe
Jan 10 08:57:27 raspberrypi kernel: [ 3307.355265] [ 2481]   107  2481    87690     6390      63     6582             0 mysqld
Jan 10 08:57:27 raspberrypi kernel: [ 3307.382308] Out of memory: Kill process 2481 (mysqld) score 94 or sacrifice child
Jan 10 08:57:27 raspberrypi kernel: [ 3307.382368] Killed process 2481 (mysqld) total-vm:350760kB, anon-rss:24180kB, file-rss:1400kB
Jan 10 09:32:34 raspberrypi kernel: [ 5414.511466] [ 2112]     0  2112      440       22       4        4             0 mysqld_safe
Jan 10 09:32:34 raspberrypi kernel: [ 5414.525084] [ 3960]   107  3960    84076    10191      54        0             0 mysqld
Jan 10 09:32:34 raspberrypi kernel: [ 5414.536306] Out of memory: Kill process 3960 (mysqld) score 74 or sacrifice child
Jan 10 09:32:34 raspberrypi kernel: [ 5414.536347] Killed process 3960 (mysqld) total-vm:336304kB, anon-rss:40200kB, file-rss:564kB
Jan 10 09:52:11 raspberrypi kernel: [ 6592.536282] [ 2112]     0  2112      440       22       4        4             0 mysqld_safe
Jan 10 09:52:11 raspberrypi kernel: [ 6592.552416] [ 4776]   107  4776    84504     9808      51        0             0 mysqld
Jan 10 09:52:11 raspberrypi kernel: [ 6592.564303] Out of memory: Kill process 4776 (mysqld) score 71 or sacrifice child
Jan 10 09:52:11 raspberrypi kernel: [ 6592.564340] Killed process 4776 (mysqld) total-vm:338016kB, anon-rss:38740kB, file-rss:512kB
```

---

### Post by nerdtron on 2015-01-11
So this is a raspberrypi? how much memory (RAM) is still free and how big is the database in the mysql?

---

### Post by iacoposk8 on 2015-01-11
has a raspberry with 512 of ram.
 the database continues to grow because unloading several tweets every minute, but I still have a lot of hard disk space

---

### Post by nerdtron on 2015-01-11
probably adding more swap memory will help? From the logs it seems that mysql is running out of memory

---

### Post by iacoposk8 on 2015-01-15
thank you

---

