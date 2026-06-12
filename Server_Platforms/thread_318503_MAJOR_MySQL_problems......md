---
title: "MAJOR MySQL problems....."
date: 2006-12-14
forum: Server Platforms
---

### Post by FXWGBill on 2006-12-14
](*,) ](*,) Hopefully this is not 'out of line' or wayyyyyyy tmi....  I have tried everything over and over and here are my notes...  I am at a total loss....  Helppppppppppppp

MySQL will not start.  If I go in and manually make the var directories and log directories, I can get it to run  in 'safe mode'.  The minute I logout and reboot, it's all gone.   Please bear with me....  These are my notes....  (I apologize in advance for the mess)

The sections are in reverse order; the newest attempts are first....  (after reboots, getting safe to run, that kind of thing...

Here we go:
NOW AM GONNA FOLLOW THIS POST:
[http://ubuntuforums.org/showthread.php?t=111292&page=2](http://ubuntuforums.org/showthread.php?t=111292&page=2)
---------------------------------------------------------------------------------------------------------------------
crazyeccentric@CrazyEccentric:~$ cd /var/lib/mysql
crazyeccentric@CrazyEccentric:/var/lib/mysql$ LS
bash: LS: command not found
crazyeccentric@CrazyEccentric:/var/lib/mysql$ ls
debian-5.0.flag  ibdata1  ib_logfile0  ib_logfile1  mysql
crazyeccentric@CrazyEccentric:/var/lib/mysql$ mv mysql mysql_bkp
crazyeccentric@CrazyEccentric:/var/lib/mysql$ ls
debian-5.0.flag  ibdata1  ib_logfile0  ib_logfile1  mysql_bkp
crazyeccentric@CrazyEccentric:/var/lib/mysql$ sudo mysql_install_db
Installing all prepared tables
Fill help tables

To start mysqld at boot time you have to copy support-files/mysql.server
to the right place for your system

PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
To do so, start the server, then issue the following commands:
/usr/bin/mysqladmin -u root password 'new-password'
/usr/bin/mysqladmin -u root -h CrazyEccentric password 'new-password'
See the manual for more instructions.

You can start the MySQL daemon with:
cd /usr ; /usr/bin/mysqld_safe &

You can test the MySQL daemon with the benchmarks in the 'sql-bench' directory:
cd sql-bench ; perl run-all-tests

Please report any problems with the /usr/bin/mysqlbug script!

The latest information about MySQL is available on the web at
[http://www.mysql.com](http://www.mysql.com)
Support MySQL by buying support/licenses at [http://shop.mysql.com](http://shop.mysql.com)
crazyeccentric@CrazyEccentric:/var/lib/mysql$
-------------------------------------------------------------------------------------------------------------------------
COMPLETE REMOVAL OF MYSQL - AGAINNNNNNN
Dec 13, 2006 - 2155

THIS time... we are gonna digress tooooooooo  version:  4.1 and see how it goes

GRRRRRRRRRRRRRRRRRRRRRRRRRRRRR  it won't let me 'back freakin up to a previous version!!

crazyeccentric@CrazyEccentric:~$ mysqld_safe
chown: changing ownership of `/var/run/mysqld': Operation not permitted
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[7329]: started

DID A   ctrl-c     and this is what I got, over and over and over.......

Could not open required defaults file: /etc/mysql/debian.cnf
Fatal error in defaults handling. Program aborted
mysqld_safe[12840]: Number of processes running now: 1
mysqld_safe[12848]: mysqld process hanging, pid 7331 - killed
mysqld_safe[12851]: restarted
rm: cannot remove `/var/run/mysqld/mysqld.sock': Permission denied
rm: cannot remove `/var/run/mysqld/mysqld.pid': Permission denied
mysqld_safe[12875]: Number of processes running now: 0
mysqld_safe[12877]: restarted
ETC.....

Tried to start it again.....   and did go in and manually remove the pid file, but it still will not start again.....

crazyeccentric@CrazyEccentric:~$ mysqld_safe
rm: cannot remove `/var/run/mysqld/mysqld.pid': Permission denied
mysqld_safe[15885]: Fatal error: Can't remove the pid file: /var/run/mysqld/mysqld.pid
mysqld_safe[15887]: Please remove it manually and start /usr/bin/mysqld_safe again
mysqld_safe[15889]: mysqld daemon not started

crazyeccentric@CrazyEccentric:~$ mysqld_safe
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[17150]: started
rm: cannot remove `/var/run/mysqld/mysqld.sock': Permission denied
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[17172]: ended
crazyeccentric@CrazyEccentric:~$ mysqld_safe
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[17261]: started
rm: cannot remove `/var/run/mysqld/mysqld.sock': Permission denied
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[17283]: ended
crazyeccentric@CrazyEccentric:~$

DEBIAN_FRONTEND=readline; export DEBIAN_FRONTEND; apt-get install --yes 'mysql-server-4.1' ;echo RESULT=$?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbd-pg-perl libqt4-core libzvt2
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  mysql-server-4.1
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
12 not fully installed or removed.
Need to get 0B/17.0MB of archives.
After unpacking 38.1MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 312190 files and directories currently installed.)
Unpacking mysql-server-4.1 (from .../mysql-server-4.1_4.1.15-1ubuntu5_i386.deb) ...
Aborting downgrade from (at least) 5.0 to 4.1.
dpkg: error processing /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
RESULT=100

IT SAYS RIGHT HERE IN THE DANG TERMINAL WINDOW FOR SYNAPTIC - 
	invoke-rc.d: unknown initscript, etc/init.d/mysql not found
AND IT FORCED ME TO INSTAL 5.0......
------------------------------------------------------------------------------------------------------
COMPLETE REMOVAL OF MYSQL
Dec 13, 2006 - 1700

Start with marking synaptic for complete removal of all MySQL components...

also removed:
amarok
bitchx
flyspray
kmformat
some Apache stuff
kmysqladmin
some php5 stuff
qt4-qtconfig
------------------------------------------------------------------------------------------------------
did a reboot and ran:
crazyeccentric@CrazyEccentric:~$ sudo dpkg --purge mysql-server
Password:
dpkg - warning: ignoring request to remove mysql-server which isn't installed.
crazyeccentric@CrazyEccentric:~$
---------------------------------------------------------------------------------------------------
Checking the Bootup manager for MySQL
This is saying that mydns is still loaded up, which uses mysql as the data storage thingy
This is weird... Synaptic says that mydns ain't even loaded up either.....

ok... some good info:
[http://www.ubuntuforums.org/showthread.php?t=304734&highlight=MySQL+will+-start](http://www.ubuntuforums.org/showthread.php?t=304734&highlight=MySQL+will+-start)
-----------------------------------------------------------------------------------------------------------
And a reboot....... anddddddddddd
Just found THIS:
-----------------------------------------
Set startup item (Dreamweaver site)
-----------------------------------------
# sudo cp /usr/local/mysql/share/mysql/mysql.server /etc/init.d/mysql
# sudo update-rc.d mysql defaults

Results of the update-rc.d command were as follows:
Adding system startup for /etc/init.d/mysql ...
/etc/rc0.d/K20mysql -> ../init.d/mysql
/etc/rc1.d/K20mysql -> ../init.d/mysql
/etc/rc6.d/K20mysql -> ../init.d/mysql
/etc/rc2.d/S20mysql -> ../init.d/mysql
/etc/rc3.d/S20mysql -> ../init.d/mysql
/etc/rc4.d/S20mysql -> ../init.d/mysql
/etc/rc5.d/S20mysql -> ../init.d/mysql

Above info came from:

[http://www.ubuntuforums.org/showthread.php?t=237377&highlight=sudo%3A+%2Fetc%2Finit.d%2Fmysql%3A+command+-found](http://www.ubuntuforums.org/showthread.php?t=237377&highlight=sudo%3A+%2Fetc%2Finit.d%2Fmysql%3A+command+-found)

HANG ONTO THESE:

[http://my.server.address/phpmyadmin](http://my.server.address/phpmyadmin)
---------------------------------------------------------------
OOOOOOOOOOOO K

10:46

Using Synaptic to install MySQL 5.0 - both server and client
Next will reboot after the install...

Synaptic says good to go.... gonna look at system monitor real quick and then reboot
	don't see it running yet in System Monitor....
Looking at Boot up manager...
	don't see MySQL anywhere in there either.... 

Reboot and see what happens.....

OK... still not in boot up manager and is NOT running in the system monitor....

Next going to do the above commands and try and get the command:
	sudo /etc/init.d/mysql start and stop to work properly...

SOOOOOOOOOOOOOOOOOO...

sudo cp /usr/local/mysql/share/mysql/mysql.server /etc/init.d/mysql

and I get:
crazyeccentric@CrazyEccentric:~$ sudo cp /usr/local/mysql/share/mysql/mysql.server /etc/init.d/mysql
cp: cannot stat `/usr/local/mysql/share/mysql/mysql.server': No such file or directory
crazyeccentric@CrazyEccentric:~$

sudo update-rc.d mysql defaults

and I get:
crazyeccentric@CrazyEccentric:~$ sudo update-rc.d mysql defaults
update-rc.d: /etc/init.d/mysql: file does not exist
crazyeccentric@CrazyEccentric:~$

Doing searches now for:
	mysql.server
So far not finding anything

OK.... Just for the sake of argument....  

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

re-install it all again....

SAYS:
Suggested packages:
  php-pear
so we'll go back and get that when 'this' is done...

===============================================================
STILL Doesn't work right.... 

Installing phpmyadmin

crazyeccentric@CrazyEccentric:~$ sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbd-pg-perl libqt4-core libzvt2
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  phpmyadmin
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/3607kB of archives.
After unpacking 14.1MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package phpmyadmin.
(Reading database ... 313303 files and directories currently installed.)
Unpacking phpmyadmin (from .../phpmyadmin_4%3a2.8.2-0.2_all.deb) ...
Setting up phpmyadmin (2.8.2-0.2) ...

crazyeccentric@CrazyEccentric:~$

REBOOT.... againnnnnnnnn

---------------------------------------------
and still get nothing....


crazyeccentric@CrazyEccentric:~$ sudo mysqld --skip-grant-tables
Password:
061213 12:11:13  InnoDB: Started; log sequence number 0 43655
061213 12:11:14 [ERROR] Can't start server : Bind on unix socket: No such file or directory
061213 12:11:14 [ERROR] Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
061213 12:11:14 [ERROR] Aborting

061213 12:11:14  InnoDB: Starting shutdown...
061213 12:11:16  InnoDB: Shutdown completed; log sequence number 0 43655
061213 12:11:16 [Note] mysqld: Shutdown complete

And it turns out that:
	/var/run/mysqld/mysqld.sock
doesn't even exist...
---------------------------------------------------------------------------
Next we try: 

MySQL initially only allows connections from the localhost (127.0.0.1). We'll need to remove that restriction if you wish to make it accessible to everyone on the internet. Open the file /etc/mysql/my.cnf 
gksudo gedit /etc/mysql/my.cnf
Find the line bind-address = 127.0.0.1 and comment it out 
...
#bind-address           = 127.0.0.1
...
MySQL comes with no root password as default. This is a huge security risk. You'll need to set one. So that the local computer gets root access as well, you'll need to set a password for that too. The local-machine-name is the name of the computer you're working on. For more information see here 
mysqladmin -u root password your-new-password

crazyeccentric@CrazyEccentric:~$ mysqladmin -u root password xxxxxx
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysq                      ld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock'                       exists!
crazyeccentric@CrazyEccentric:~$

and AGAIN.... No:    /var/run/mysqld/mysqld.sock

ok.... I made an empty file at this point, searching for exactly what I need in there....

NEED TO TRY AND MAKE ONE.....

Poking at straws................

crazyeccentric@CrazyEccentric:~$ mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)
crazyeccentric@CrazyEccentric:~$

OK>>>> DOIN SEARCHES....

var - the file I made is found
etc - nothing
dev - nothing
lib - nothing
srv - nothing


ps aux | grep mysqld:
crazyeccentric@CrazyEccentric:~$ ps aux | grep mysqld
1000     25089  0.0  0.0   2796   764 pts/4    S+   13:41   0:00 grep mysqld


TRYING AGAIN
------------------------------------------------------------------------------------------------
sudo apt-get install --reinstall mysql-server mysql-client libmysqlclient12-dev
	note that the dev file was not previously installed....

sudo /etc/init.d/mysql restart

-------------------------------------------------------------------------------------------------------
crazyeccentric@CrazyEccentric:~$ sudo /etc/init.d/mysql restart
sudo: /etc/init.d/mysql: command not found
crazyeccentric@CrazyEccentric:~$

-----------------------------------------------------------------------------------------------------------------------

crazyeccentric@CrazyEccentric:~$ sudo dpkg-reconfigure mysql-server
crazyeccentric@CrazyEccentric:~$ sudo /etc/init.d/mysql restart
sudo: /etc/init.d/mysql: command not found
crazyeccentric@CrazyEccentric:~$

------------------------------------------------------------------------------------------------------------------------

crazyeccentric@CrazyEccentric:~$ netstat -tap | grep mysql
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
crazyeccentric@CrazyEccentric:~$

--------------------------------------------------------------------------------------------------------------------------

crazyeccentric@CrazyEccentric:~$ ps -ef | grep mysql
1000     13888  5647  0 12:40 ?        00:00:00 /usr/bin/mysql-admin
1000     28663 12761  0 14:00 pts/4    00:00:00 grep mysql


mysqld --version

crazyeccentric@CrazyEccentric:~$ mysqld --version
mysqld  Ver 5.0.24a-Debian_9-log for pc-linux-gnu on i486 (Debian etch distribution)
crazyeccentric@CrazyEccentric:~$

--------------------------------------------------------------------------------------------------------
NEXT

Re: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'

I'm having a very similar problem and have boiled it down to this:

- I add the directory mysql to /var/run/
- I set owner to root rwx (read,write,execute)
- I set group to mysql rwx
- I enter command: mysqld as root and mysql runs great.

MINE DOESN'T:

crazyeccentric@CrazyEccentric:~$ mysqld
061213 14:20:21 [Warning] Can't create test file /var/lib/mysql/CrazyEccentric.lower-test
061213 14:20:21  InnoDB: Started; log sequence number 0 43655
061213 14:20:21 [ERROR] mysqld: Can't create/write to file '/var/lib/mysql/CrazyEccentric.pid' (Errcode: 13)
061213 14:20:21 [ERROR] Can't start server: can't create PID file: Permission denied
crazyeccentric@CrazyEccentric:~$


----------------------------------------------------------------------------------------------------------------





----------------------------------------------------------------------------------------------------------------------------------------------------------

crazyeccentric@CrazyEccentric:~$ sudo mysqld
Password:
061213 14:26:12 [ERROR] Fatal error: Please read "Security" section of the manual to find out how to run mysqld as root!

061213 14:26:12 [ERROR] Aborting

061213 14:26:12 [Note] mysqld: Shutdown complete

crazyeccentric@CrazyEccentric:~$

---------------------------------------------------------------------------------------------------------------------------------------------------------

mysqld  Ver 5.0.24a-Debian_9-log for pc-linux-gnu on i486 (Debian etch distribution)
crazyeccentric@CrazyEccentric:~$ mysqld
061213 14:20:21 [Warning] Can't create test file /var/lib/mysql/CrazyEccentric.lower-test
061213 14:20:21  InnoDB: Started; log sequence number 0 43655
061213 14:20:21 [ERROR] mysqld: Can't create/write to file '/var/lib/mysql/CrazyEccentric.pid' (Errcode: 13)
061213 14:20:21 [ERROR] Can't start server: can't create PID file: Permission denied
crazyeccentric@CrazyEccentric:~$ sudo mysqld
Password:
061213 14:26:12 [ERROR] Fatal error: Please read "Security" section of the manual to find out how to run mysqld as root!

061213 14:26:12 [ERROR] Aborting

061213 14:26:12 [Note] mysqld: Shutdown complete

crazyeccentric@CrazyEccentric:~$ cat /etc/mysql/my.cnf | grep .sock
cat: /etc/mysql/my.cnf: No such file or directory
crazyeccentric@CrazyEccentric:~$ sudo netstat -tap | grep mysql
crazyeccentric@CrazyEccentric:~$ sudo netstat -tap | grep mysql
crazyeccentric@CrazyEccentric:~$
crazyeccentric@CrazyEccentric:~$ ps -ef | grep mysql
1000      2266 29945  0 14:33 pts/4    00:00:00 grep mysql
crazyeccentric@CrazyEccentric:~$ sudo mysqladmin -u root password xxxxxx
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)' ----------------
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
crazyeccentric@CrazyEccentric:~$ cat /etc/mysql/my.cnf | grep address
cat: /etc/mysql/my.cnf: No such file or directory
crazyeccentric@CrazyEccentric:~$ cat /etc/mysql/my.cnf | grep address
#bind-address           = 127.0.0.1
crazyeccentric@CrazyEccentric:~$ cat /etc/mysql/my.cnf | grep user
# - "~/.my.cnf" to set user-specific options.
user            = mysql 

-------------------------------------------------------------------------------------------------------------------------------------------------

changed my.cnf.bak back to my.cnf

Reboot:  13Dec06 @ 1809

----------------------------------------------------------------------------------------------------------------------------------------------------
NEXTTTTTTTTTTTTTTTT - Looking at the info in this forum post:

[http://www.ubuntuforums.org/showthread.php?t=296068&highlight=mysqld.sock](http://www.ubuntuforums.org/showthread.php?t=296068&highlight=mysqld.sock)








WENT TO THIS:

[http://ubuntuforums.org/showthread.php?t=111292](http://ubuntuforums.org/showthread.php?t=111292)

And tried to get it to run in safe mode:

crazyeccentric@CrazyEccentric:~$ mysqld_safe
mkdir: cannot create directory `/var/run/mysqld': Permission denied
chown: cannot access `/var/run/mysqld': No such file or directory
chmod: cannot access `/var/run/mysqld': No such file or directory
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[10227]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[10249]: ended
crazyeccentric@CrazyEccentric:~$


It doesn't like 'things' either.....

gonna try modifying the permissions that failed:   with sudo gnome-commander


START WITH:

mkdir: cannot create directory `/var/run/mysqld': Permission denied - am going to manually make the directory and
	give permissions to mysql  OKKKKK  set everything owner/groups to mysql now to look at permissions
	FOR THE MOMENT:  Setting permissions so EVERYBODY can read write and excute.

OK... AGAIN:

crazyeccentric@CrazyEccentric:~$ mysqld_safe
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[11961]: started

DID  a ctrl-c   trying to get the prompt back and got:

Could not open required defaults file: /etc/mysql/debian.cnf
Fatal error in defaults handling. Program aborted
mysqld_safe[12093]: Number of processes running now: 1
mysqld_safe[12101]: mysqld process hanging, pid 11963 - killed
mysqld_safe[12104]: restarted

YESSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS

mysqld_safe  is now runninggggggggggggggg

and I can sign in with KMySQLAdmin using:

Host: localhost
username: root
password: XXXXXX
port:3306	

yesssss - verified it again
NOWWWWWWWWWWWWW

crazyeccentric@CrazyEccentric:~$ ps -ef | grep mysql
1000     11903  5957  0 18:21 pts/2    00:00:00 /bin/sh /usr/bin/mysqld_safe
1000     12106 11903  0 18:22 pts/2    00:00:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
1000     12110 11903  0 18:22 pts/2    00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
1000     12801  5647  0 18:25 ?        00:00:01 kmysqladmin -caption Mysqladm -icon kmysqladmin.png -miniicon kmysqladmin.png
1000     14153 14098  0 18:32 pts/4    00:00:00 grep mysql
crazyeccentric@CrazyEccentric:~$

OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO   K.....

gonna kill it and see if mysqld will work....  In fact... gonna do a reboot!!  

And it doesn't work.... hmmmmmmmmm


gonna rename that 'sock' file I made...  

DANGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGG

IT'S GONE... directory and file, etc....  I read that somewhere.... that... I'll find it
TRYING :


crazyeccentric@CrazyEccentric:~$ mysqld
061213 19:14:57 [Warning] One can only use the --user switch if running as root

061213 19:14:57  InnoDB: Started; log sequence number 0 43655
061213 19:14:57 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
061213 19:14:57 [Note] Starting crash recovery...
061213 19:14:57 [Note] Crash recovery finished.
061213 19:14:58 [ERROR] Can't start server : Bind on unix socket: No such file or directory
061213 19:14:58 [ERROR] Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
061213 19:14:58 [ERROR] Aborting

061213 19:14:58  InnoDB: Starting shutdown...
061213 19:15:00  InnoDB: Shutdown completed; log sequence number 0 43655
061213 19:15:00 [Note] mysqld: Shutdown complete

crazyeccentric@CrazyEccentric:~$

NOPE...

TRYING safe mode again....


crazyeccentric@CrazyEccentric:~$ mysqld_safe
mkdir: cannot create directory `/var/run/mysqld': Permission denied
chown: cannot access `/var/run/mysqld': No such file or directory
chmod: cannot access `/var/run/mysqld': No such file or directory
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[15358]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[15377]: ended
crazyeccentric@CrazyEccentric:~$  

AND THERE IT WENT AGAIN.......

OOOOOOOOOOOOOOOOOOO KKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKK
OOOOOOOOOOOOOOOOOOOO KKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKK

I am gonna backup to version 4.1  as I am seeing some posts that are saying that it works when they do that......

Here goes

Gonna use Synaptic and then reboot and double check the --purge setting.....

closing everything I don't need down......................


===============================================================================================
===============================================================================================
================================================================================================
sudo: /etc/init.d/mysql: command not found
crazyeccentric@CrazyEccentric:~$ sudo /etc/init.d/mysql stop
Password:
sudo: /etc/init.d/mysql: command not found
crazyeccentric@CrazyEccentric:~$ /usr/bin/mysqld --skip-grant-tables --user=root
bash: /usr/bin/mysqld: No such file or directory
crazyeccentric@CrazyEccentric:~$ mysqld --skip-grant-tables
061211 15:20:11 [Warning] Can't create test file /var/lib/mysql/CrazyEccentric.lower-test
061211 15:20:11 [Warning] One can only use the --user switch if running as root

mysqld: File '/var/log/mysql/mysql-bin.index' not found (Errcode: 13)
061211 15:20:11 [ERROR] Aborting

061211 15:20:11 [Note] mysqld: Shutdown complete

crazyeccentric@CrazyEccentric:~$ mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
crazyeccentric@CrazyEccentric:~$ SET PASSWORD FOR root@'localhost' = PASSWORD('password')
bash: syntax error near unexpected token `('
crazyeccentric@CrazyEccentric:~$ SET PASSWORD FOR root@'localhost' = PASSWORD('harley')
bash: syntax error near unexpected token `('
crazyeccentric@CrazyEccentric:~$ SET PASSWORD FOR root@'localhost' = PASSWORD(harley)
bash: syntax error near unexpected token `('
crazyeccentric@CrazyEccentric:~$ SET PASSWORD FOR root@localhost = PASSWORD(harley)
bash: syntax error near unexpected token `('
crazyeccentric@CrazyEccentric:~$ UPDATE mysql.user SET Password=PASSWORD('harley') WHERE User='root';
bash: syntax error near unexpected token `('
crazyeccentric@CrazyEccentric:~$ mysql start
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
crazyeccentric@CrazyEccentric:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
crazyeccentric@CrazyEccentric:~$ sudo /etc/init.d/mysql start
Password:
sudo: /etc/init.d/mysql: command not found
crazyeccentric@CrazyEccentric:~$ sudo apt-get install mysql-server
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mydns-mysql (1.1.0-3) ...
/etc/mydns.conf created/modified. See mydns.conf(5) for details.
A backup of the old config file is at /etc/mydns.conf.dpkg-old. Values
were preserved, except for database (database,db-*)
and distribution-specific information (user, group, pidfile).
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Creating database...
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
dpkg: error processing mydns-mysql (--configure):
 subprocess post-installation script returned error exit status 1
Setting up spampd (2.30-11) ...
An override for "/var/cache/spampd" already exists, aborting
Warning: statoverride couldn't be created for /var/cache/spampd
An override for "/etc/spampd.conf" already exists, aborting
Warning: statoverride couldn't be created for /etc/spampd.conf
 * ERROR: Insufficient privileges. Retry as root
invoke-rc.d: initscript spampd, action "start" failed.
dpkg: error processing spampd (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 mydns-mysql
 spampd
E: Sub-process /usr/bin/dpkg returned an error code (1)
crazyeccentric@CrazyEccentric:~$ gksudo gedit /etc/mysql/my.cnf
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
crazyeccentric@CrazyEccentric:~$ mysqladmin -u root password your-new-password
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
crazyeccentric@CrazyEccentric:~$ mysqladmin -u harley
mysqladmin  Ver 8.41 Distrib 5.0.24a, for pc-linux-gnu on i486
Copyright (C) 2000 MySQL AB & MySQL Finland AB & TCX DataKonsult AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Administration program for the mysqld daemon.
Usage: mysqladmin [OPTIONS] command command....
  -c, --count=#       Number of iterations to make. This works with -i
                      (--sleep) only.
  -#, --debug[=name]  Output debug log. Often this is 'd:t:o,filename'.
  -f, --force         Don't ask for confirmation on drop database; with
                      multiple commands, continue even if an error occurs.
  -C, --compress      Use compression in server/client protocol.
  --character-sets-dir=name
                      Directory where character sets are.
  --default-character-set=name
                      Set the default character set.
  -?, --help          Display this help and exit.
  -h, --host=name     Connect to host.
  -p, --password[=name]
                      Password to use when connecting to server. If password is
                      not given it's asked from the tty. WARNING: Providing a
                      password on command line is insecure as it is visible
                      through /proc to anyone for a short time.
  -P, --port=#        Port number to use for connection.
  --protocol=name     The protocol of connection (tcp,socket,pipe,memory).
  -r, --relative      Show difference between current and previous values when
                      used with -i. Currently works only with extended-status.
  -O, --set-variable=name
                      Change the value of a variable. Please note that this
                      option is deprecated; you can set variables directly with
                      --variable-name=value.
  -s, --silent        Silently exit if one can't connect to server.
  -S, --socket=name   Socket file to use for connection.
  -i, --sleep=#       Execute commands again and again with a sleep between.
  --ssl               Enable SSL for connection (automatically enabled with
                      other flags). Disable with --skip-ssl.
  --ssl-ca=name       CA file in PEM format (check OpenSSL docs, implies
                      --ssl).
  --ssl-capath=name   CA directory (check OpenSSL docs, implies --ssl).
  --ssl-cert=name     X509 cert in PEM format (implies --ssl).
  --ssl-cipher=name   SSL cipher to use (implies --ssl).
  --ssl-key=name      X509 key in PEM format (implies --ssl).
  --ssl-verify-server-cert
                      Verify server's "Common Name" in its cert against
                      hostname used when connecting. This option is disabled by
                      default.
  -u, --user=name     User for login if not current user.
  -v, --verbose       Write more information.
  -V, --version       Output version information and exit.
  -E, --vertical      Print output vertically. Is similar to --relative, but
                      prints output vertically.
  -w, --wait[=#]      Wait and retry if connection is down.
  --connect_timeout=#
  --shutdown_timeout=#

Variables (--variable-name=value)
and boolean options {FALSE|TRUE}  Value (after reading options)
--------------------------------- -----------------------------
count                             0
force                             FALSE
compress                          FALSE
character-sets-dir                (No default value)
default-character-set             (No default value)
host                              (No default value)
port                              3306
relative                          FALSE
socket                            /var/run/mysqld/mysqld.sock
sleep                             0
ssl                               FALSE
ssl-ca                            (No default value)
ssl-capath                        (No default value)
ssl-cert                          (No default value)
ssl-cipher                        (No default value)
ssl-key                           (No default value)
ssl-verify-server-cert            FALSE
user                              harley
verbose                           FALSE
vertical                          FALSE
connect_timeout                   43200
shutdown_timeout                  3600

Default options are read from the following files in the given order:
/etc/mysql/my.cnf ~/.my.cnf /etc/mysql/my.cnf
The following groups are read: mysqladmin client
The following options may be given as the first argument:
--print-defaults        Print the program argument list and exit
--no-defaults           Don't read default options from any options file
--defaults-file=#       Only read default options from the given file #
--defaults-extra-file=# Read this file after the global files are read

Where command is a one or more of: (Commands may be shortened)
  create databasename   Create a new database
  debug                 Instruct server to write debug information to log
  drop databasename     Delete a database and all its tables
  extended-status       Gives an extended status message from the server
  flush-hosts           Flush all cached hosts
  flush-logs            Flush all logs
  flush-status          Clear status variables
  flush-tables          Flush all tables
  flush-threads         Flush the thread cache
  flush-privileges      Reload grant tables (same as reload)
  kill id,id,...        Kill mysql threads
  password new-password Change old password to new-password, MySQL 4.1 hashing.
  old-password new-password Change old password to new-password in old format.

  ping                  Check if mysqld is alive
  processlist           Show list of active threads in server
  reload                Reload grant tables
  refresh               Flush all tables and close and open logfiles
  shutdown              Take server down
  status                Gives a short status message from the server
  start-slave           Start slave
  stop-slave            Stop slave
  variables             Prints variables available
  version               Get version info from server
crazyeccentric@CrazyEccentric:~$ sudo /etc/init.d/mysql restart
sudo: /etc/init.d/mysql: command not found
crazyeccentric@CrazyEccentric:~$ gksudo gedit /etc/mysql/my.cnf
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
crazyeccentric@CrazyEccentric:~$ mysqladmin -u root password harley
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
crazyeccentric@CrazyEccentric:~$ gksudo gedit /var/run/mysqld/mysqld.sock

crazyeccentric@CrazyEccentric:~$ sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup

crazyeccentric@CrazyEccentric:~$ sudo gedit /etc/apt/sources.list


crazyeccentric@CrazyEccentric:~$ sudo apt-get update





[http://www.ubuntuforums.org/showthread.php?t=296068&highlight=var%2Frun%2Fmysqld%2Fmysqld.sock](http://www.ubuntuforums.org/showthread.php?t=296068&highlight=var%2Frun%2Fmysqld%2Fmysqld.sock)


/etc/mysql/my.cnf



#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "/var/lib/mysql/my.cnf" to set server-specific options or
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# [http://dev.mysql.com/doc/mysql/en/server-system-variables.html](http://dev.mysql.com/doc/mysql/en/server-system-variables.html)

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
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking
#
# For compatibility to other Debian packages that still use
# libmysqlclient10 and libmysqlclient12.
old_passwords	= 1
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
#bind-address		= 127.0.0.1
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
#
# * Query Cache Configuration
#
query_cache_limit	= 1048576
query_cache_size        = 16777216
query_cache_type        = 1
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
#
# The following can be used as easy to replay backup logs or for replication.
#server-id		= 1
log_bin			= /var/log/mysql/mysql-bin.log
# WARNING: Using expire_logs_days without bin_log crashes the server! See README.Debian!
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * BerkeleyDB
#
# According to an MySQL employee the use of BerkeleyDB is now discouraged
# and support for it will probably cease in the next versions.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
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
# The following configuration is read by the ndbd storage daemons,
# not from the ndb_mgmd management daemon.
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1

](*,) ](*,)

---

### Post by 0x29a on 2006-12-14
The forums seem to be full of mysql issues with nobody being able to come up with any solutions. All the stuff I've read talks about uninstalling 5.x and installing 4.x, or any number of things. And what effect will uninstalling and reinstalling just mysql 5.x have on a new 6.06.1 LAMP server installation? Can't be good. What's the point of doing a LAMP installation if I have to ham-fist things just to come up with no answers to a problem everyone is having?  

I've spent my entire day trying to find answers to the "Can't connect to local MySQL server through socket" problem and nothing. What a nightmare. mysqld.sock is a dynamic file created at runtime, so just creating it with touch is not going to work as some have alluded to.

I'm too frustrated to be constructive beyond saying "very nice and detailed post."

 I'm done venting. Thanks, and good luck.

---

### Post by Bill007 on 2006-12-15
Kia Ora 

 Part of the fun in doing all of this is solving the problem, Isnt it
Just think how you will feel when you get the right result

You need to look at your logs for clues  this file can help  /var/log/syslog

This is a great forum and I have solved many problems thru it Thanks to the members


But there are other  forum resources try [sitepoint]("http://www.sitepoint.com/forums/") for mysql support These guys are good also PHP support is awesome always a couple a thousand people about to share your plight happy hunting

Regards Bill007

---

### Post by 0x29a on 2006-12-17
Bill007,
I know. I was just frustrated. Thank you for the perspective. I've gone over syslog repeatedly, among other stuff but I haven't been very bright about it, I suppose. I've found a lot of good advise in these forums as well. 

Anyway, I'm one of those that lost power during the windstorms in the Northwest US, and much of the internet hubs are still messed up. For instance, I try to traceroute to my gateway from a local coffee shop and it loops between two routers after three hops....hehe. At least the power is back on and we have heat. I can put the water bottles and coleman stove away now for another month. :)

Thanks again,
Andrew

---

### Post by dmizer on 2007-01-14
not sure exactly why you're having problems.  just to test things, i loaded mysql-server, mysql-admin, and mysql-query-browser from the repos and have a working mysql server.  no hangups at all.
```
$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                 [ ok ] 
 * Starting MySQL database server mysqld                                 [ ok ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
```

now i frankly haven't done anything with this.  it's simply installed and i verified that it works.  so i'm not too sure what the difference is.  i made NO changes to any directory structures, i did not have to copy anything from another location to get mysql to appear in the /etc/init.d directory.

i followed this guide nearly to the letter: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_MYSQL_Database_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_MYSQL_Database_Server).  the exception is that every time it said "apt-get" i used "aptitude".  you should begin the same habit.  aptitude is far superior in being able to add remove and manipulate packages.

this box is edgy with the 2.6.17-10-generic kernel

---

