---
title: "Mysql Multiple servers setup questions"
date: 2009-02-04
forum: Server Platforms
---

### Post by theDaveTheRave on 2009-02-04
Dear All.

I am trying to set up multiple MySQL servers on my terminal.

ultimately I want to convert this to a master / slave setup between 2 machines, but for now I have some questions.

I have successfully got mutliple servers running. but how do I access them independently of one another??

here is the important part of the </etc/mysql/my.cnf> file

```


[mysqld_multi]
mysqld		= /usr/bin/mysqld_safe
mysqladmin	= /usr/bin/mysqladmin
log		= /var/lib/mysql/mysqld_multi.log
user		= root
password	= EjdZmfAcer


[mysqld_safe]

socket		= /var/run/mysqld/mysqld.sock
nice		= 0
relay-log	= mysql-relay-bin
err-log		= /var/lib/mysql/mysql_safe_nostart.log
log-error	= /var/lib/mysql/mysql_safe_err.log
user		= mysql

[mysqld2]
server-id	= 2
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
#socket		= /var/run/mysqld/mysqld.sock # allready set on line 44.
port		= 3308
basedir		= /usr
[COLOR="Blue"]datadir		= /var/lib/mysql[/COLOR]
tmpdir		= /tmp
language	= /usr/share/mysql/english
default-storage-engine = innodb

[mysqld5]
server-id	= 5
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid5
#socket		= All servers will use the same local socket file for connecting

port		= 3309
basedir		= /usr
[COLOR="Blue"]datadir		= /var/lib/mysql2[/COLOR]
tmpdir		= /tmp
language	= /usr/share/mysql/english
default-storage-engine = innodb

[mysqld357]
server-id	= 357
mysqld		= /usr/bin/mysqld_safe
#socket		= All servers will use the same local socket file for connecting
port 		= 1357
pid-file	= /var/lib/mysqldTest/mysqld.pid
basedir		= /usr
[COLOR="Blue"]datadir		= /var/lib/mysqlTest/mysql[/COLOR]
language	= /usr/share/mysql/english
tmpdir		= /tmp
user		= mysql
bind-address 	= 'testDB'
default-storage-engine = innodb


```

You are probably wondering why I set up 3 instances, this is because at first I couldn't get the [mysqld357] server to run, but I have now solved that problem.

so I know that they are running from 

```

davem@Dartagnon:~$ mysqld_multi report
Reporting MySQL servers
MySQL server from group: mysqld2 is running
MySQL server from group: mysqld5 is running
MySQL server from group: mysqld357 is running
davem@Dartagnon:~$

```

which would all seem rather good to me... however
if I log into MySQL with the following

```
davem@Dartagnon:~$ mysql -u davem -p -P 1357
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 24
Server version: 5.0.51a-3ubuntu5.4-log (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>

```

and then call the following function...

```

mysql> show variables like "%port%";
+---------------------+-------+
| Variable_name       | Value |
+---------------------+-------+
| innodb_support_xa   | ON    | 
| large_files_support | ON    | 
| port                | 3308  | 
+---------------------+-------+
3 rows in set (0.01 sec)

mysql>show variables like "%server%";
+----------------------+-------------------+
| Variable_name        | Value             |
+----------------------+-------------------+
| character_set_server | latin1            | 
| collation_server     | latin1_swedish_ci | 
| server_id            | 2                 | 
+----------------------+-------------------+
3 rows in set (0.00 sec) 

```

which would seem to suggest I am in fact looking at the first server available in the list.

In a way this isn't a surprise, as they are all using the same <base directory> and hence are all looking at and retrieving data from the same <information_schema> tables.

But here is my problem.

I can select and add data to any table on any of the servers, from any server

any help would be appreciated, so as I can separate all the server instances.

thanks in advance

David

Edit #1 ...


So I've been thinking about all this.... and I've just had the thought that maybee I need to physically install a second MySQL server onto my terminal in a separate place?

would this sound correct??

Another thing I suddenly realised... I have the servers set up with different <datadir = /var/~...> settings. So I checked to see if there was a sub folder for my new <test357> database. And there was, but only in the data ddirectory for the the server on [mysqld2] not in the data directory of < /var/lib/mysql/mysqlTest > which is what I was hoping to see!

So now I have tried a third access method, 

```

davem@Dartagnon:~$ mysql -u davem -p -P3358

```
which I assumed would not allow me to gain access to the MySQL server as I don't have a server on port 3358.... but

```

Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 5.0.51a-3ubuntu5.4 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| MGI_Mouse          | 
| fastaFishing       | 
| genefocus          | 
| identitylinks      | 
| mysql              | 
| mysqlTest          | 
| old_to_new         | 
| test357            | 
+--------------------+
9 rows in set (0.16 sec)

mysql> 

```

As you can see I can get in, and view all my databases!

I am really scratching my head on this one.... I guess I am going to have to install a second instance of MySQL.... but I'm not sure how to do this.... I will report back shortly.

Edit #2....

Ok so now I've been really "geeky" I've downloaded and installed the newest version of MySQL (ie version 6- alpha.

I used the install procedure to send it to a separate place on my HDD (inside the home/MySQL/MySQL6 folder), and the /home is on a separate partition, so if I refresh my pc I won't have to do a complete re-install of all of this....I hope....

but now I have another issue.

I want both mysql5.### and mysql6 to start up on boot.

they both want to look at the same config file (ie the one above) that lives in </etc/mysql/my.cnf> so now my issue is how do I make them look at different my.cnf files??

I'm sure I can work out 2 little scripts to run the mysqld_safe deamon's at startup (obviously the one for the new MySQL6 version sits in </home/mysql/MySQL6/bin> and the general one sits on <usr/bin/> (according to the <locate mysqld_safe> that I have just done). Which all seems fair enough.

In fact I have just decided to check some things.
```

davem@Dartagnon:~$ ps aux |grep mysql
root      5372  0.0  0.1   1772   524 ?        S    08:47   0:00 [COLOR="Blue"]/bin/sh /home/msql/MySQL6/bin/mysqld_safe --datadir=/home/msql/MySQL6/var --pid-file=/home/msql/MySQL6/var/Dartagnon.pid[/COLOR]
mysql     5450  0.0  2.7  45136 14044 ?        Sl   08:47   0:00 /home/msql/MySQL6/libexec/mysqld --basedir=/home/msql/MySQL6 --datadir=/home/msql/MySQL6/var --user=mysql --log-error=/var/lib/mysql/mysql_safe_err.log --pid-file=/home/msql/MySQL6/var/Dartagnon.pid --socket=/var/run/mysqld/mysqld.sock
davem     8655  0.0  0.1   3004   744 pts/0    D+   09:14   0:00 grep mysql

```

Which would certainly suggest that there is a server running using the MySQL6 install on the correct data directory, and when I log into MySQL it just shows the test and information schema databases... which is cool

so now I start my "other" mysql5, and then check the ps aux
```

davem@Dartagnon:~$ sudo mysqld_multi start
[sudo] password for davem: 
davem@Dartagnon:~$ ps aux |grep mysql
root      5372  0.0  0.1   1772   524 ?        S    08:47   0:00 /bin/sh /home/msql/MySQL6/bin/mysqld_safe --datadir=/home/msql/MySQL6/var --pid-file=/home/msql/MySQL6/var/Dartagnon.pid
mysql     5450  0.0  2.5  45424 13084 ?        Sl   08:47   0:00 /home/msql/MySQL6/libexec/mysqld --basedir=/home/msql/MySQL6 --datadir=/home/msql/MySQL6/var --user=mysql --log-error=/var/lib/mysql/mysql_safe_err.log --pid-file=/home/msql/MySQL6/var/Dartagnon.pid --socket=/var/run/mysqld/mysqld.sock
davem     8660  2.3  4.8  49304 24572 ?        Sl   09:15   0:01 /usr/bin/mysql-query-browser
davem     8669  2.4  4.3  47292 21908 ?        S    09:15   0:01 /usr/bin/mysql-query-browser
root      8682  0.0  0.1   1772   520 pts/0    S    09:16   0:00 /bin/sh /usr/bin/mysqld_safe --server-id=2 --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --port=3308 --basedir=/usr --datadir=/var/lib/mysql --tmpdir=/tmp --language=/usr/share/mysql/english --default-storage-engine=innodb --log-error=/var/lib/mysql/mysqlServer2.err --log-long --bind-address=Dartagnon --key_buffer_size=64M --max_allowed_packet=16M --thread_stack=128 --thread_cache_size=8 --query_cache_limit=1M --query_cache_size=16M --log_bin=/var/log/mysql/mysql-bin.log --expire_logs_days=21 --max_binlog_size=100M --skip-bdb
mysql     8914  0.3  4.2 176012 21284 pts/0    Sl   09:16   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3308 --socket=/var/run/mysqld/mysqld.sock --server-id=2 --tmpdir=/tmp --language=/usr/share/mysql/english --default-storage-engine=innodb --log-error=/var/lib/mysql/mysqlServer2.err --log-long --bind-address=Dartagnon --key_buffer_size=64M --max_allowed_packet=16M --thread_stack=128 --thread_cache_size=8 --query_cache_limit=1M --query_cache_size=16M --log_bin=/var/log/mysql/mysql-bin.log --expire_logs_days=21 --max_binlog_size=100M --skip-bdb
davem     8970  0.0  0.1   3012   780 pts/0    R+   09:16   0:00 grep mysql
davem@Dartagnon:~$ 
[code]

now all I need to do is get them both to run as start u!

so a shell script is going to be required I guess!?

A quick question... should I write down how / why I have done this?? and put it here as an extended howto!?? what do you all think?

David.

Edit Feb.10th.

Ok so I thought that this was all working hapily. I haven't changed anything anywhere in my set up and I can't access any of instances of MySQL?

If i try to access anything I get the same message about the server being unavailable.

I've tried a reboot, but doesn't seem to help.

I can't even use the mysqld_multi tool...

[code]
davem@Dartagnon:~$ sudo mysqld_multi report
[sudo] password for davem: 
Unknown option: port
Error with an option, see mysqld_multi --help for more info.
davem@Dartagnon:~$ sudo mysqld_multi stop
Unknown option: port
Error with an option, see mysqld_multi --help for more info.
davem@Dartagnon:~$ sudo mysqld_multi start
Unknown option: port
Error with an option, see mysqld_multi --help for more info.
davem@Dartagnon:~$ 

```

so where do I go now?

is anyone out there thinking that i have a curious problem?

---

### Post by theDaveTheRave on 2009-02-11
Hello again all.

I've complete my setup but seem to be having some issues.

here is what i did.

I downloaded and installed MySQL6 from source.

I put the installation into the < /home/mysql/MySQL6/ > folder, and all the relevent data directories sit there also.

by way of proof I have done a < ps aux | grep mysql> and have the folowing
```

davem@Dartagnon:~$ ps aux | grep mysql
root      5245  0.0  0.1   1772   528 ?        S    07:50   0:00 /bin/sh /home/msql/MySQL6/bin/mysqld_safe --datadir=/home/msql/MySQL6/var --pid-file=/home/msql/MySQL6/var/Dartagnon.pid
mysql     5323  0.0  2.3  45136 12056 ?        Sl   07:50   0:00 /home/msql/MySQL6/libexec/mysqld --basedir=/home/msql/MySQL6 --datadir=/home/msql/MySQL6/var --user=mysql --log-error=/var/lib/mysql/mysql_safe_err.log --pid-file=/home/msql/MySQL6/var/Dartagnon.pid --socket=/var/run/mysqld/mysqld.sock
davem     7200  0.0  0.1   3012   780 pts/0    R+   09:09   0:00 grep mysql
d

```

Everything seems to work OK, I have the MySQL6 install runing at boot time.

but I also had an original version of MySQL5 (from the repositories) sitting in < /usr > with the data directory in < /var/lib/mysql >

I want to start this up at the same time, but can live with starting it manually for now, using mysqld_start, here is the output from that followed by another ps aux...

```

davem@Dartagnon:~$ sudo mysqld_multi start
davem@Dartagnon:~$ ps aux |grep mysql
root      5245  0.0  0.1   1772   528 ?        S    07:50   0:00 /bin/sh /home/msql/MySQL6/bin/mysqld_safe --datadir=/home/msql/MySQL6/var --pid-file=/home/msql/MySQL6/var/Dartagnon.pid
mysql     5323  0.0  2.3  45136 12056 ?        Sl   07:50   0:00 /home/msql/MySQL6/libexec/mysqld --basedir=/home/msql/MySQL6 --datadir=/home/msql/MySQL6/var --user=mysql --log-error=/var/lib/mysql/mysql_safe_err.log --pid-file=/home/msql/MySQL6/var/Dartagnon.pid --socket=/var/run/mysqld/mysqld.sock
root      7315  0.0  0.1   1772   520 pts/1    S    09:20   0:00 /bin/sh /usr/bin/mysqld_safe --server-id=2 --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --port=3308 --basedir=/usr --datadir=/var/lib/mysql --tmpdir=/tmp --language=/usr/share/mysql/english --default-storage-engine=innodb --log-error=/var/lib/mysql/mysqlServer2.err --log-long --bind-address=Dartagnon --key_buffer_size=64M --max_allowed_packet=16M --thread_stack=128 --thread_cache_size=8 --query_cache_limit=1M --query_cache_size=16M --log_bin=/var/log/mysql/mysql-bin.log --expire_logs_days=21 --max_binlog_size=100M --skip-bdb
mysql     7468  1.2  4.2 176012 21300 pts/1    Sl   09:20   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3308 --socket=/var/run/mysqld/mysqld.sock --server-id=2 --tmpdir=/tmp --language=/usr/share/mysql/english --default-storage-engine=innodb --log-error=/var/lib/mysql/mysqlServer2.err --log-long --bind-address=Dartagnon --key_buffer_size=64M --max_allowed_packet=16M --thread_stack=128 --thread_cache_size=8 --query_cache_limit=1M --query_cache_size=16M --log_bin=/var/log/mysql/mysql-bin.log --expire_logs_days=21 --max_binlog_size=100M --skip-bdb
davem     7603  0.0  0.1   3008   756 pts/1    R+   09:21   0:00 grep mysql
davem@Dartagnon:~$ 

```
which all seems fine, on the face of it... BUT

I can't access the MySQL6 instance from the local machine?

and I can't access the MySQL5 instance from a remote machine, but i used to be able to do so?

How do I "remove" the instance of MySQL6 and get back to my OLD config??

thanks in advance

---

### Post by theDaveTheRave on 2009-02-11
Ok then...

I opened another thread to understand how to remove the MySQL6 install, it is based here...
[http://ubuntuforums.org/showthread.php?p=6715508#post6715508]("http://ubuntuforums.org/showthread.php?p=6715508#post6715508")

this is a copy of what I am currently up to...
> 

Interestingly I think it may have explained why I have my problem.

I searched for make...

Code:

davem@Dartagnon:~$ locate make | grep mysql
/home/msql/MySQL6/mysql-test/include/maria_make_snapshot.inc
/home/msql/MySQL6/mysql-test/include/maria_make_snapshot_for_comparison.inc
/home/msql/MySQL6/mysql-test/include/maria_make_snapshot_for_feeding_recovery.inc
/usr/local/mysql-6.0.9-alpha/cmd-line-utils/libedit/makelist
/usr/local/mysql-6.0.9-alpha/cmd-line-utils/libedit/makelist.sh
/usr/local/mysql-6.0.9-alpha/extra/yassl/taocrypt/benchmark/make.bat
/usr/local/mysql-6.0.9-alpha/extra/yassl/taocrypt/test/make.bat
/usr/local/mysql-6.0.9-alpha/extra/yassl/testsuite/make.bat
/usr/local/mysql-6.0.9-alpha/man/make_win_bin_dist.1
/usr/local/mysql-6.0.9-alpha/mysql-test/include/maria_make_snapshot.inc
/usr/local/mysql-6.0.9-alpha/mysql-test/include/maria_make_snapshot_for_comparison.inc
/usr/local/mysql-6.0.9-alpha/mysql-test/include/maria_make_snapshot_for_feeding_recovery.inc
/usr/local/mysql-6.0.9-alpha/scripts/make_binary_distribution
/usr/local/mysql-6.0.9-alpha/scripts/make_binary_distribution.sh
/usr/local/mysql-6.0.9-alpha/scripts/make_sharedlib_distribution
/usr/local/mysql-6.0.9-alpha/scripts/make_sharedlib_distribution.sh
/usr/local/mysql-6.0.9-alpha/scripts/make_win_bin_dist
/usr/local/mysql-6.0.9-alpha/storage/innobase/pars/make_bison.sh
/usr/local/mysql-6.0.9-alpha/storage/innobase/pars/make_flex.sh
/usr/local/mysql-6.0.9-alpha/storage/ndb/config/make-win-dsw.sh
/usr/local/mysql-6.0.9-alpha/strings/strmake-sparc.s
/usr/local/mysql-6.0.9-alpha/strings/strmake.c
/usr/local/mysql-6.0.9-alpha/strings/strmake.lo
/usr/local/mysql-6.0.9-alpha/strings/strmake.o
/usr/local/mysql-6.0.9-alpha/strings/.deps/strmake.Plo
/usr/local/mysql-6.0.9-alpha/strings/.libs/strmake.o
/usr/local/mysql-6.0.9-alpha/win/mysql_manifest.cmake
davem@Dartagnon:~$ cd /usr/local
davem@Dartagnon:/usr/local$

which would suggest I only have a single install of MySQL6 on my system.

then I remembered that during the install of the source I did the usual thing of creating a symbolic link, which shows up in ls.

[code]
davem@Dartagnon:/usr/local$ ls -la
total 52
drwxr-xr-x 13 mysql mysql 4096 2009-02-05 12:02 .
drwxr-xr-x 12 root root 4096 2008-11-14 15:04 ..
drwxr-xr-x 2 mysql mysql 4096 2008-07-02 12:16 bin
drwxr-xr-x 2 mysql mysql 4096 2008-07-02 12:16 etc
drwxr-xr-x 2 mysql mysql 4096 2008-07-02 12:16 games
drwxr-xr-x 13 mysql mysql 4096 2008-11-17 22:41 glassfish-v2ur2
drwxr-xr-x 2 mysql mysql 4096 2008-07-02 12:16 include
drwxr-xr-x 4 mysql mysql 4096 2008-11-18 15:26 lib
lrwxrwxrwx 1 mysql mysql 9 2008-11-13 19:22 man -> share/man
lrwxrwxrwx 1 mysql mysql 17 2009-02-05 12:02 mysql -> mysql-6.0.9-alpha
drwxrwxrwx 32 mysql mysql 4096 2009-02-05 12:49 mysql-6.0.9-alpha
drwxr-xr-x 21 mysql mysql 4096 2008-11-17 22:40 netbeans-6.1
drwxr-xr-x 2 mysql mysql 4096 2008-07-02 12:16 sbin
drwxr-xr-x 12 mysql mysql 4096 2009-01-24 22:47 share
drwxr-xr-x 2 mysql mysql 4096 2008-07-02 12:16 src
davem@Dartagnon:/usr/local$

[code]

so I'm going to ask a different question now.... but can you answer in my original thread on multi server setup which is here...

http://ubuntuforums.org/showthread.php?t=1059736

so my question is this... I'm going to repeat the post on that thread also, and refer back to here.

If I have 2 separate instances how do I get them both to run at the same time??

I realise that I need to have 2 separate </usr/local/mysql> links, one pointing to MySQL6 and the other at MySQL5.

I guess I will call them mysql and mysql5 respectively.

So I know that the standard install of MySQl from the repositories sends the database files etc into the < var/lib/mysql> directory.

but now I'm getting a little stuck..... I really feel I should be able to have both sets of server running simultaneously.... !!!

I'm going to keep "playing" for a while...



---

