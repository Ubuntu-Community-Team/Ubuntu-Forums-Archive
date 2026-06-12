---
title: "MySQL won't start"
date: 2009-07-06
forum: Server Platforms
---

### Post by Zeikcied on 2009-07-06
I wanted to play around a bit with a private web server (I'm behind a router, so as long as I don't forward the ports I should be okay).  But I'm having trouble with MySQL.

I don't know if it's because MySQL-common files were already installed (I believe they come as the base in Kubuntu Jaunty) or what.  But when I run apt-get or dpkg to install mysql-server, it doesn't work properly.

I get the prompts for a database password, which I set.  Then dpkg shows this:

```
Setting up mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2) ...
 * Stopping MySQL database server mysqld                                [ OK ]
 * Reloading AppArmor profiles ...                                      [ OK ]
 * Starting MySQL database server mysqld                                [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
```

The System Log shows this:

```
2009-07-06 19:29:54	***-desktop	mysqld_safe[1774]	/usr/bin/mysql_install_db: line 433:  1789 Done                    { echo "use mysql;"; cat $create_system_tables $fill_system_tables; }
2009-07-06 19:29:54	***-desktop	mysqld_safe[1774]	      1791                       | eval "$filter_cmd_line"
2009-07-06 19:29:54	***-desktop	mysqld_safe[1774]	      1793 Segmentation fault      | $mysqld_install_cmd_line > /dev/null
2009-07-06 19:29:54	***-desktop	mysqld_safe[1774]	Installation of system tables failed!
```

Then later it shows this:

```
2009-07-06 19:30:11	***-desktop	/etc/init.d/mysql[2346]	0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
2009-07-06 19:30:11	***-desktop	/etc/init.d/mysql[2346]	^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
2009-07-06 19:30:11	***-desktop	/etc/init.d/mysql[2346]	error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
2009-07-06 19:30:11	***-desktop	/etc/init.d/mysql[2346]	Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

I have no idea what this all means.  I don't know anything about servers.  I just wanted to play around with phpBB and a couple other things without having to pay for a web host. :(

---

### Post by LepeKaname on 2009-07-06
>  subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured

It seems that mysql-server-5.0 was not installed. Run this command:

**sudo aptitude install mysql-server-5.0**

If that doesn't fix it, reinstall mysql again:

[B]sudo aptitude purge mysql-server-5.0 mysql-server mysql-common mysql-client-5.0 mysql-server-core-5.0
sudo aptitude install mysql-server-5.0 mysql-server mysql-common mysql-client-5.0 mysql-server-core-5.0[/B]

That should fix it. The first command "purge" will remove your mysql configuration files too.

If still you have problems, maybe you have some problem in your repositories.

If you can't get it installed (for some reason), you could try to install mysql-server-5.1 available for jaunty.

---

### Post by Zeikcied on 2009-07-06
> **LepeKaname said:**
> It seems that mysql-server-5.0 was not installed. Run this command:

**sudo aptitude install mysql-server-5.0**

If that doesn't fix it, reinstall mysql again:

[B]sudo aptitude purge mysql-server-5.0 mysql-server mysql-common mysql-client-5.0 mysql-server-core-5.0
sudo aptitude install mysql-server-5.0 mysql-server mysql-common mysql-client-5.0 mysql-server-core-5.0[/B]

That should fix it. The first command "purge" will remove your mysql configuration files too.

If still you have problems, maybe you have some problem in your repositories.

If you can't get it installed (for some reason), you could try to install mysql-server-5.1 available for jaunty.

When I try to install mysql-server-5.0 via apt-get, I get this:

```
Setting up mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2) ...
 * Stopping MySQL database server mysqld                                [ OK ]
/var/lib/dpkg/info/mysql-server-5.0.postinst: line 28: 19288 Segmentation fault      $MYSQL_BOOTSTRAP < $tfile
 * Reloading AppArmor profiles ...                                      [ OK ]
 * Starting MySQL database server mysqld                                [fail]
invoke-rc.d: initscript mysql, action "start" failed.
```

I don't always get that Seg fault error, but I sometimes do.

Anyway, I don't really think it'd be smart to remove mysql-common.  Because when I use apt-get remove mysql-common, it wants to remove 187 packages. :(  Kubuntu Jaunty, thanks to KDE4, comes with mysql-common and mysql-server-core-5.0, but not any other mysql package.

I'm not using any special repositories for the MySQL packages, so what I'm getting is straight from the official Jaunty repositories.

---

### Post by LepeKaname on 2009-07-07
According to this:
[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/301104](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/301104)

> apt-get remove libc6-i686
may solve the issue.

I hope this help you...

---

### Post by Zeikcied on 2009-07-07
> **LepeKaname said:**
> According to this:
[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/301104](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/301104)


may solve the issue.

I hope this help you...

I was going to try that, but apt wanted to also remove ubuntu-minimal, and I wasn't sure if it's okay to get rid of that.

EDIT: That didn't seem to work. :(

---

### Post by LepeKaname on 2009-07-07
> **Zeikcied said:**
> I was going to try that, but apt wanted to also remove ubuntu-minimal, and I wasn't sure if it's okay to get rid of that.

EDIT: That didn't seem to work. :(

ubuntu-minimal is safe to be removed (it is just a meta-package). 

Is strange... I have Jaunty and I didn't have any problem with mysql... 

Please take a look at these logs (anything related to mysqld or apparmor):
    /var/log/daemon.log
    /var/log/kern.log
    /var/log/syslog

Can you post these files? (just mask passwords information)
    /etc/mysql/my.cnf

---

### Post by Zeikcied on 2009-07-07
Okay.  I posted some of the daemon.log earlier, but I could copy everything.  This part is from yesterday:

```
ul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: /usr/bin/mysql_install_db: line 433: 19644 Done                    { echo "use mysql;"; cat $create_system_tables $fill_system_tables; }
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]:      19646                       | eval "$filter_cmd_line"
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]:      19648 Segmentation fault      | $mysqld_install_cmd_line > /dev/null
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: Installation of system tables failed!
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: 
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: Examine the logs in /var/lib/mysql for more information.
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: You can try to start the mysqld daemon with:
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: /usr/sbin/mysqld --skip-grant &
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: and use the command line tool
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: /usr/bin/mysql to connect to the mysql
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: database and look at the grant tables:
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: 
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: shell> /usr/bin/mysql -u root mysql
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: mysql> show tables
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: 
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: Try 'mysqld --help' if you have problems with paths. Using --log
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: gives you a log in /var/lib/mysql that may be helpful.
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: 
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: The latest information about MySQL is available on the web at
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: http://www.mysql.com
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: Please consult the MySQL manual section: 'Problems running mysql_install_db',
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: and the manual section that describes problems on your OS.
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: Another information source is the MySQL email archive.
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: Please check all of the above before mailing us!
Jul  6 16:27:55 darthbrandon-desktop mysqld_safe[19629]: And if you do mail us, you MUST use the /usr/bin/mysqlbug script!
Jul  6 16:27:56 darthbrandon-desktop mysqld_safe[19848]: started
Jul  6 16:27:56 darthbrandon-desktop mysqld_safe[19853]: ended
Jul  6 16:28:11 darthbrandon-desktop /etc/init.d/mysql[20027]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jul  6 16:28:11 darthbrandon-desktop /etc/init.d/mysql[20027]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jul  6 16:28:11 darthbrandon-desktop /etc/init.d/mysql[20027]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jul  6 16:28:11 darthbrandon-desktop /etc/init.d/mysql[20027]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

From kern.log:

```
Jul  6 16:27:56 darthbrandon-desktop kernel: [94019.806719] type=1505 audit(1246912075.997:16): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=19721
Jul  6 16:27:56 darthbrandon-desktop kernel: [94019.858496] type=1505 audit(1246912076.049:17): operation="profile_replace" name="/usr/sbin/mysqld-akonadi" name2="default" pid=19726
```

The syslog seems to just have the same stuff as the other two, just combined.

My my.cnf file should be the default installed file.  I did alter it, but I undid my changes.  But you wanted me to post it, so...  (I don't believe there are any passwords in it.)

```
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover		= BACKUP
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log		= /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 1
#log_bin			= /var/log/mysql/mysql-bin.log
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
#
# * Federated
#
# The FEDERATED storage engine is disabled since 5.0.67 by default in the .cnf files
# shipped with MySQL distributions (my-huge.cnf, my-medium.cnf, and so forth).
#
skip-federated
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/
```

---

### Post by abaden on 2009-07-07
What happens when you do...
```
sudo dpkg --get-selections | grep mysql
```

You may want to try searching for MySQL processes that are still running, killing them, purging all MySQL packages from the system, and reinstalling again. I've had problems on Ubuntu Server when I either had a zombie MySQL process or other packages that don't play nice with MySQL installed.


Alex

---

### Post by Zeikcied on 2009-07-08
> **abaden said:**
> What happens when you do...
```
sudo dpkg --get-selections | grep mysql
```

You may want to try searching for MySQL processes that are still running, killing them, purging all MySQL packages from the system, and reinstalling again. I've had problems on Ubuntu Server when I either had a zombie MySQL process or other packages that don't play nice with MySQL installed.


Alex

I get:
```
libapache2-mod-auth-mysql                       install
libdbd-mysql-perl                               install
libmysqlclient15off                             install
libqt4-sql-mysql                                install
mysql-client-5.0                                install
mysql-common                                    install
mysql-server                                    install
mysql-server-5.0                                install
mysql-server-core-5.0                           install
php5-mysql                                      install
```

I don't think I can remove mysql-common as much of KDE4 depends on that package.  I don't think that package is really an issue, as I've had no problems with any of the programs that make use of it.  mysql-server-core-5.0 is used by a lot less KDE4 apps, but I've had no issues with programs that use that, either.

---

### Post by abaden on 2009-07-08
Yes, that's true, removing too much MySQL will damage KDE. Is this thread of any help? 

[http://ubuntuforums.org/showthread.php?p=7373648](http://ubuntuforums.org/showthread.php?p=7373648)


Alex

---

### Post by Zeikcied on 2009-07-08
> **abaden said:**
> Yes, that's true, removing too much MySQL will damage KDE. Is this thread of any help? 

[http://ubuntuforums.org/showthread.php?p=7373648](http://ubuntuforums.org/showthread.php?p=7373648)


Alex
No, because I haven't rebooted since I installed it.  That solution seems to be for people having problems with it not starting upon booting.  I'm just trying to get it started, period.  dpkg still lists it as not fully configured, because the post-installation script isn't able to start mysql, so the dpkg configuration technically fails.

---

### Post by abaden on 2009-07-08
When was the last time you upgraded the system? All my boxes are 8.04, so I haven't really played with 9 yet, but perhaps the version of MySQL you haven't doesn't play nicely with KDE. 

What does "apt-cache policy mysql-server-5.0" output?


Alex

---

### Post by Zeikcied on 2009-07-09
> **abaden said:**
> When was the last time you upgraded the system? All my boxes are 8.04, so I haven't really played with 9 yet, but perhaps the version of MySQL you haven't doesn't play nicely with KDE. 

What does "apt-cache policy mysql-server-5.0" output?


Alex

```
mysql-server-5.0:
  Installed: 5.1.30really5.0.75-0ubuntu10.2
  Candidate: 5.1.30really5.0.75-0ubuntu10.2
  Version table:
 *** 5.1.30really5.0.75-0ubuntu10.2 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        100 /var/lib/dpkg/status
     5.1.30really5.0.75-0ubuntu10 0
        500 http://us.archive.ubuntu.com jaunty/main Packages
```

I upgraded to Jaunty (a fresh install) a little over a month ago, I think.  Maybe in the middle or end of May.  I forget exactly when.  I keep the packages updated, too.

I don't know if the MySQL server would conflict with a GUI, though.  The packages that are dependencies of KDE4 apps appear to be just fine.

---

### Post by Zeikcied on 2009-07-14
After reading the man page for apt-get, I figured out how to reinstall a package from the command line.

So I ran apt-get install --reinstall mysql-server-core-5.0, and now mysqld starts.

So it's all fixed, and I didn't have to mess up KDE4. :D  Thanks for the help!

---

