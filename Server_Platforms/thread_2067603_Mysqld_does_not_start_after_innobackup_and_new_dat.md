---
title: "Mysqld does not start after innobackup and new datadir"
date: 2012-10-07
forum: Server Platforms
---

### Post by Tunkkaamo on 2012-10-07
Hello.

Running 10.04 server and mysql 5.01.

I experimendted innobackup which made a one backup file of all databases.

Tested restoring the database by first stopping mysql service (stop mysql), extracting the backup to a new dir (/var/lib/data), modified the /etc/mysql/my.cnf to point there and to check the mysqld.sock to point to /var/run/mysqld/mysqld.sock .

```
[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

[mysqld]
datadir         = /var/lib/data


```

however the mysqld refuses to restart:

/etc/init.d/mysql start will not work after upstart implementation and start mysql does not work either.
Even reboot does not help.

The error remains:

```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```
When I try to connect to mysql from command line.

The file mysql.sock does not exist anymore.
In fact if I try :

```
sudo find / -name mysqld.sock

```
Gives no result. 

In one post it was adviced to point to the socket file "manually2
in my.cnf file, but as you can see from above this did not help.

I would like to use innobackup, as the backup and restore are superfast. This socket problem need sto be solved first though.

Any ideas appreciated.

---

### Post by mootpoint on 2012-10-07
myhost# touch /var/run/mysqld/mysqld.sock
myhost# /etc/init.d/mysql start

m00t

---

### Post by Crafty Kisses on 2012-10-08
Try 
```
mysql_config --socket
/tmp/mysql.sock

```
Restart and do
```
mysql -u root -p
```
Give permissions:
```
sudo chown -R mysql /var/run/mysqld/
```
Try again.

---

### Post by Tunkkaamo on 2012-10-08
> **mootpoint said:**
> myhost# touch /var/run/mysqld/mysqld.sock
myhost# /etc/init.d/mysql start

m00t

Unfortunately this did not help.
The service does not start.

If I give the /etc/init.d/mysql start or
the service mysql start command, the command line just stays stuck for a while. Service does not start and error remains the same:[B]
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'.[/B]

The file does exist now though, but is zero bytes.

---

### Post by Tunkkaamo on 2012-10-08
> **Crafty Kisses said:**
> Try 
```
mysql_config --socket
/tmp/mysql.sock

```
Restart and do
```
mysql -u root -p
```
Give permissions:
```
sudo chown -R mysql /var/run/mysqld/
```
Try again.

Abit strange but the mysql_config is nowhere to be found.

```
# find / -name mysql_config
```

Results nothing.

Thanks for all suggestions so far anyway.

---

### Post by Crafty Kisses on 2012-10-09
Can I see
```
ps -A
```

---

### Post by Tunkkaamo on 2012-10-10
When I started the machine, Mysql qwas on the list.
After I tried to login, I got the usual socket error. then mysql process disappeared from the list.

PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 cpuset
   12 ?        00:00:00 khelper
   13 ?        00:00:00 netns
   14 ?        00:00:00 async/mgr
   15 ?        00:00:00 pm
   17 ?        00:00:00 sync_supers
   18 ?        00:00:00 bdi-default
   19 ?        00:00:00 kintegrityd/0
   20 ?        00:00:00 kintegrityd/1
   21 ?        00:00:00 kblockd/0
   22 ?        00:00:00 kblockd/1
   23 ?        00:00:00 kacpid
    24 ?        00:00:00 kacpi_notify
   25 ?        00:00:00 kacpi_hotplug
   26 ?        00:00:00 ata/0
   27 ?        00:00:00 ata/1
   28 ?        00:00:00 ata_aux
   29 ?        00:00:00 ksuspend_usbd
   30 ?        00:00:00 khubd
   31 ?        00:00:00 kseriod
   32 ?        00:00:00 kmmcd
   35 ?        00:00:00 khungtaskd
   36 ?        00:00:00 kswapd0
   37 ?        00:00:00 ksmd
   38 ?        00:00:00 aio/0
   39 ?        00:00:00 aio/1
   40 ?        00:00:00 ecryptfs-kthrea
   41 ?        00:00:00 crypto/0
   42 ?        00:00:00 crypto/1
   49 ?        00:00:00 scsi_eh_0
   50 ?        00:00:00 scsi_eh_1
   52 ?        00:00:00 scsi_eh_2
   53 ?        00:00:00 scsi_eh_3
   56 ?        00:00:00 kstriped
   57 ?        00:00:00 kmpathd/0
    58 ?        00:00:00 kmpathd/1
   59 ?        00:00:00 kmpath_handlerd
   60 ?        00:00:00 ksnapd
   61 ?        00:00:00 kondemand/0
   62 ?        00:00:00 kondemand/1
   63 ?        00:00:00 kconservative/0
   64 ?        00:00:00 kconservative/1
  278 ?        00:00:00 scsi_eh_4
  279 ?        00:00:00 usb-storage
  281 ?        00:00:00 i915
  447 ?        00:00:00 kdmflush
  448 ?        00:00:00 kcryptd_io
  450 ?        00:00:01 kcryptd
  491 ?        00:00:00 kdmflush
  495 ?        00:00:00 kdmflush
  509 ?        00:00:00 flush-8:0
  533 ?        00:00:00 jbd2/dm-2-8
  534 ?        00:00:00 ext4-dio-unwrit
  535 ?        00:00:00 ext4-dio-unwrit
  582 ?        00:00:00 upstart-udev-br
  585 ?        00:00:00 udevd
  731 ?        00:00:00 udevd
  768 ?        00:00:00 udevd
   839 ?        00:00:00 kpsmoused
  889 ?        00:00:00 hd-audio0
  923 ?        00:00:00 flush-1:15
  924 ?        00:00:00 flush-1:14
  925 ?        00:00:00 flush-1:13
  926 ?        00:00:00 flush-1:12
  927 ?        00:00:00 flush-1:11
  928 ?        00:00:00 flush-1:10
  929 ?        00:00:00 flush-1:9
  930 ?        00:00:00 flush-1:8
  931 ?        00:00:00 flush-1:7
  932 ?        00:00:00 flush-1:6
  933 ?        00:00:00 flush-1:5
  934 ?        00:00:00 flush-1:4
  935 ?        00:00:00 flush-1:3
  936 ?        00:00:00 flush-1:2
  937 ?        00:00:00 flush-1:1
  938 ?        00:00:00 flush-1:0
  939 ?        00:00:00 flush-251:2
  993 ?        00:00:00 jbd2/sda1-8
  994 ?        00:00:00 ext4-dio-unwrit
  995 ?        00:00:00 ext4-dio-unwrit
 1008 ?        00:00:00 rsyslogd
 1050 tty4     00:00:00 getty
 1057 tty5     00:00:00 getty
 1062 tty2     00:00:00 getty
 1064 tty3     00:00:00 getty
 1069 tty6     00:00:00 getty
 1096 ?        00:00:00 atd
 1097 ?        00:00:00 cron
 1116 ?        00:00:00 postgres
 1151 ?        00:00:00 postgres
 1152 ?        00:00:00 postgres
 1153 ?        00:00:00 postgres
 1154 ?        00:00:00 postgres
 1188 ?        00:00:00 dhclient3
 1222 ?        00:00:00 sshd
 1234 ?        00:00:00 apache2
 1243 ?        00:00:00 apache2
 1244 ?        00:00:00 apache2
 1245 ?        00:00:00 apache2
 1246 ?        00:00:00 apache2
 1247 ?        00:00:00 apache2
 1262 tty1     00:00:00 getty
 1282 ?        00:00:00 sshd
 1373 ?        00:00:00 sshd
  1116 ?        00:00:00 postgres
 1151 ?        00:00:00 postgres
 1152 ?        00:00:00 postgres
 1153 ?        00:00:00 postgres
 1154 ?        00:00:00 postgres
 1188 ?        00:00:00 dhclient3
 1222 ?        00:00:00 sshd
 1234 ?        00:00:00 apache2
 1243 ?        00:00:00 apache2
 1244 ?        00:00:00 apache2
 1245 ?        00:00:00 apache2
 1246 ?        00:00:00 apache2
 1247 ?        00:00:00 apache2
 1262 tty1     00:00:00 getty
 1282 ?        00:00:00 sshd
 1373 ?        00:00:00 sshd
 1374 pts/0    00:00:00 bash
 1397 pts/0    00:00:00 su
 1404 pts/0    00:00:00 bash
 1579 ?        00:00:00 sh
 1599 ?        00:00:00 sleep
 1600 pts/0    00:00:00 ps
 1601 pts/0    00:00:00 bash

---

### Post by Tunkkaamo on 2012-10-14
When I look at the original var/lib/mysql folder and the one made by innobackup, in innobackup folder there are no ib_logfile0 and ib_logfile1 files.

Maybe I should add some options on the backup script so that the innobackup would create these?

---

