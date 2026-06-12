---
title: "Mysql broken beyond reason please help"
date: 2011-12-15
forum: Server Platforms
---

### Post by Tystick86 on 2011-12-15
Hello everyone,

So I had installed through apt-get mysql long ago. It worked for a very long time. Then me and my friend started learning drupal together and something very interesting and at this point frustrating for me happened. I used Drush which is there little comand line pocket interface for creating new drupal sites and doing other things with it. Well I guess I should have looked at there code first because its supposed to install a new web site in the current directory and create a Data base with the same name. It instead broke mysql. I no longer have the mysqld.sock file and I cant purge mysql to try and reinstall it.

so here is the most information I can give you:

$ sudo stop mysql

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

$ sudo start mysql

sudo mysql stop
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

$ ps -e | grep mysql
(nothing)

$nmap localhost


Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-12-15 15:27 MST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00032s latency).
rDNS record for 127.0.0.1: localhost.localdomain
Not shown: 993 closed ports
PORT    STATE SERVICE
21/tcp  open  ftp
22/tcp  open  ssh
110/tcp open  pop3
143/tcp open  imap
443/tcp open  https
631/tcp open  ipp
902/tcp open  iss-realsecure

Nmap done: 1 IP address (1 host up) scanned in 0.12 seconds

When it first happened I purged mysql and reinstalled and it worked again. Then the socket mysteriously disappeared again and now I cant purge it because the package management is broken.

Anyone know of a good way to completely remove mysql and reinstall when you cant kill the ghost processes of mysql that keep apt-get from being able to purge it.

Thank you

---

### Post by Tystick86 on 2011-12-15
Yeah I solved it.

So I went back in forth between

$ sudo apt-get -f install

and 

$ sudo apt-get -f --purge remove mysql-server mysql-common mysql-client

and it finally completely removed mysql and reinstalled and its up now. My 10 hour quest is finished though I am still curious wtf happened. If any one has some enlightening insights I would be all ears.

here is some dump if your board.

-----------------------------------------
[tyrel@Yoda: dir: etc time: 15:40:14]
-----------------------------------------
om: sudo apt-get --purge remove mysql-server mysql-common mysql-client libmysqlclient15-dev libmysql-ruby
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libmysqlclient-dev' instead of 'libmysqlclient15-dev'
Package libmysql-ruby is not installed, so not removed
Package libmysqlclient-dev is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libmysqlclient16 : Depends: mysql-common (>= 5.1.49-1ubuntu8.1) but it is not going to be installed
 mysql-client-5.1 : Depends: mysql-common (>= 5.1.49-1ubuntu8.1) but it is not going to be installed
 mysql-server-5.1 : PreDepends: mysql-common (>= 5.1.49-1ubuntu8.1) but it is not going to be installed
 syscp : Depends: apache2 or
                  lighttpd but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

-----------------------------------------
[tyrel@Yoda: dir: etc time: 15:41:02]
-----------------------------------------
om: sudo apt-get --purge remove mysql-server mysql-common mysql-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libmysqlclient16 : Depends: mysql-common (>= 5.1.49-1ubuntu8.1) but it is not going to be installed
 mysql-client-5.1 : Depends: mysql-common (>= 5.1.49-1ubuntu8.1) but it is not going to be installed
 mysql-server-5.1 : PreDepends: mysql-common (>= 5.1.49-1ubuntu8.1) but it is not going to be installed
 syscp : Depends: apache2 or
                  lighttpd but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

-----------------------------------------
[tyrel@Yoda: dir: etc time: 15:41:31]
-----------------------------------------
om: sudo apt-get -f --purge remove mysql-server mysql-common mysql-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libmysqlclient16 : Depends: mysql-common (>= 5.1.49-1ubuntu8.1) but it is not going to be installed
 mysql-client-5.1 : Depends: mysql-common (>= 5.1.49-1ubuntu8.1) but it is not going to be installed
 mysql-server-5.1 : PreDepends: mysql-common (>= 5.1.49-1ubuntu8.1) but it is not going to be installed
 syscp : Depends: apache2 or
                  lighttpd but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

-----------------------------------------
[tyrel@Yoda: dir: etc time: 15:41:54]
-----------------------------------------
om: sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  apache2 apache2-mpm-worker apache2-utils apache2.2-bin apache2.2-common
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom
The following NEW packages will be installed
  apache2 apache2-mpm-worker apache2-utils apache2.2-bin apache2.2-common
0 upgraded, 5 newly installed, 0 to remove and 171 not upgraded.
1 not fully installed or removed.
Need to get 2,328B/3,203kB of archives.
After this operation, 10.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  apache2.2-bin apache2-utils apache2.2-common apache2-mpm-worker apache2
Install these packages without verification [y/N]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main apache2-mpm-worker amd64 2.2.16-1ubuntu3.4 [2,328B]
Fetched 2,328B in 0s (3,993B/s)             
Selecting previously deselected package apache2.2-bin.
(Reading database ... 321743 files and directories currently installed.)
Unpacking apache2.2-bin (from .../apache2.2-bin_2.2.16-1ubuntu3.4_amd64.deb) ...
Selecting previously deselected package apache2-utils.
Unpacking apache2-utils (from .../apache2-utils_2.2.16-1ubuntu3.4_amd64.deb) ...
Selecting previously deselected package apache2.2-common.
Unpacking apache2.2-common (from .../apache2.2-common_2.2.16-1ubuntu3.4_amd64.deb) ...
Selecting previously deselected package apache2-mpm-worker.
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.2.16-1ubuntu3.4_amd64.deb) ...
Selecting previously deselected package apache2.
Unpacking apache2 (from .../apache2_2.2.16-1ubuntu3.4_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Setting up apache2.2-bin (2.2.16-1ubuntu3.4) ...
Setting up apache2-utils (2.2.16-1ubuntu3.4) ...
Setting up apache2.2-common (2.2.16-1ubuntu3.4) ...
Enabling site default.
Enabling module alias.
Enabling module autoindex.
Enabling module dir.
Enabling module env.
Enabling module mime.
Enabling module negotiation.
Enabling module setenvif.
Enabling module status.
Enabling module auth_basic.
Enabling module deflate.
Enabling module authz_default.
Enabling module authz_user.
Enabling module authz_groupfile.
Enabling module authn_file.
Enabling module authz_host.
Enabling module reqtimeout.
Setting up apache2-mpm-worker (2.2.16-1ubuntu3.4) ...
 * Starting web server apache2                                                                                                                               [ OK ] 
Setting up apache2 (2.2.16-1ubuntu3.4) ...
Setting up syscp (1.4.2.1-2) ...
 * Reloading web server config apache2                                                                                                                       [ OK ] 
dbconfig-common: writing config to /etc/dbconfig-common/syscp.conf
Replacing config file /etc/syscp/config-db.php with new version
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2).
unable to connect to mysql server.
error encountered creating user:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
dbconfig-common: syscp configure: ignoring errors from here forwards
populating database via scriptfile...  PHP Notice:  Use of undefined constant INSTALLATION_ROOT - assumed 'INSTALLATION_ROOT' in /usr/share/dbconfig-common/scripts/syscp/install/mysql on line 23
Establishing connection failed, exiting<br />
mysql error number: 2013<br />
mysql error desc: Lost connection to MySQL server at 'reading initial communication packet', system error: 111<br />
Time/date: 15/12/2011 03:43 PM<br />
Script: <br />
Referer: <br />
done.
dbconfig-common: flushing administrative password

-----------------------------------------
[tyrel@Yoda: dir: etc time: 15:43:20]
-----------------------------------------
om: sudo apt-get -f --purge remove mysql-server mysql-common mysql-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apache2-mpm-worker apache2-utils apache2 apache2.2-common apache2.2-bin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  libdbd-mysql-perl* libmysqlclient16* libsasl2-modules-sql* mysql-client* mysql-client-5.1* mysql-client-core-5.1* mysql-common* mysql-server* mysql-server-5.1*
  mysql-server-core-5.1* php5-mysql* postfix-mysql* proftpd-mod-mysql* syscp*
0 upgraded, 0 newly installed, 14 to remove and 171 not upgraded.
After this operation, 63.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 322294 files and directories currently installed.)
Removing syscp ...
dbconfig-common: dumping mysql database syscp to /var/tmp/syscp.syscp.2011-12-15-15.43.mysql.bRkEHv.
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2).
unable to connect to mysql server.
error encountered dumping database:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
dbconfig-common: syscp remove: aborted.
dbconfig-common: flushing administrative password
dpkg: error processing syscp (--purge):
 subprocess installed pre-removal script returned error exit status 1
Removing mysql-server ...
Removing mysql-server-5.1 ...
stop: Unknown instance: 
Purging configuration files for mysql-server-5.1 ...
Removing mysql-client ...
Removing mysql-client-5.1 ...
Removing libdbd-mysql-perl ...
Removing postfix-mysql ...
Removing proftpd-mod-mysql ...
Removing mysql-server-core-5.1 ...
Removing mysql-client-core-5.1 ...
Removing libsasl2-modules-sql ...
dpkg: libmysqlclient16: dependency problems, but removing anyway as you requested:
 php5-mysql depends on libmysqlclient16 (>= 5.1.21-1).
Removing libmysqlclient16 ...
Purging configuration files for libmysqlclient16 ...
Removing mysql-common ...
Purging configuration files for mysql-common ...
dpkg: warning: while removing mysql-common, directory '/etc/mysql' not empty so not removed.
dpkg: php5-mysql: dependency problems, but removing anyway as you requested:
 syscp depends on php5-mysql.
Removing php5-mysql ...
Purging configuration files for php5-mysql ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 syscp
E: Sub-process /usr/bin/dpkg returned an error code (1)

-----------------------------------------
[tyrel@Yoda: dir: etc time: 15:44:15]
-----------------------------------------
om: sudo apt-get -f --purge remove mysql-server mysql-common mysql-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-client is not installed, so not removed
Package mysql-common is not installed, so not removed
Package mysql-server is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 syscp : Depends: php5-mysql but it is not going to be installed
         Depends: mysql-server
         Recommends: postfix-mysql but it is not going to be installed
         Recommends: libsasl2-modules-sql but it is not going to be installed
         Recommends: proftpd-mod-mysql but it is not going to be installed
         Recommends: mysql-client
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

-----------------------------------------
[tyrel@Yoda: dir: etc time: 15:44:30]
-----------------------------------------
om: sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libdbd-mysql-perl libmysqlclient16 mysql-client-5.1 mysql-client-core-5.1 mysql-common mysql-server mysql-server-5.1 mysql-server-core-5.1 php5-mysql
Suggested packages:
  tinyca mailx
The following NEW packages will be installed
  libdbd-mysql-perl libmysqlclient16 mysql-client-5.1 mysql-client-core-5.1 mysql-common mysql-server mysql-server-5.1 mysql-server-core-5.1 php5-mysql
0 upgraded, 9 newly installed, 0 to remove and 171 not upgraded.
Need to get 0B/23.1MB of archives.
After this operation, 58.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  mysql-common libmysqlclient16 libdbd-mysql-perl mysql-client-core-5.1 mysql-client-5.1 mysql-server-core-5.1 mysql-server-5.1 mysql-server php5-mysql
Install these packages without verification [y/N]? y
Preconfiguring packages ...
Selecting previously deselected package mysql-common.
(Reading database ... 321984 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_5.1.49-1ubuntu8.1_all.deb) ...
Selecting previously deselected package libmysqlclient16.
Unpacking libmysqlclient16 (from .../libmysqlclient16_5.1.49-1ubuntu8.1_amd64.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.016-1_amd64.deb) ...
Selecting previously deselected package mysql-client-core-5.1.
Unpacking mysql-client-core-5.1 (from .../mysql-client-core-5.1_5.1.49-1ubuntu8.1_amd64.deb) ...
Selecting previously deselected package mysql-client-5.1.
Unpacking mysql-client-5.1 (from .../mysql-client-5.1_5.1.49-1ubuntu8.1_amd64.deb) ...
Selecting previously deselected package mysql-server-core-5.1.
Unpacking mysql-server-core-5.1 (from .../mysql-server-core-5.1_5.1.49-1ubuntu8.1_amd64.deb) ...
Processing triggers for man-db ...
Setting up mysql-common (5.1.49-1ubuntu8.1) ...
Selecting previously deselected package mysql-server-5.1.
(Reading database ... 322181 files and directories currently installed.)
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.49-1ubuntu8.1_amd64.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.49-1ubuntu8.1_all.deb) ...
Selecting previously deselected package php5-mysql.
Unpacking php5-mysql (from .../php5-mysql_5.3.3-1ubuntu9.7_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up libmysqlclient16 (5.1.49-1ubuntu8.1) ...
Setting up libdbd-mysql-perl (4.016-1) ...
Setting up mysql-client-core-5.1 (5.1.49-1ubuntu8.1) ...
Setting up mysql-client-5.1 (5.1.49-1ubuntu8.1) ...
Setting up mysql-server-core-5.1 (5.1.49-1ubuntu8.1) ...
Setting up mysql-server-5.1 (5.1.49-1ubuntu8.1) ...
mysql start/running, process 15193
Setting up mysql-server (5.1.49-1ubuntu8.1) ...
Setting up php5-mysql (5.3.3-1ubuntu9.7) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

