---
title: "MySQL problems with 16.04"
date: 2016-10-31
forum: Server Platforms
---

### Post by PuK84 on 2016-10-31
Howdy all,

Am attempting to set up a MySQL server on my Ubuntu 16.04 server and everywhere says it should be easy. Unfortunately for me, its not as easy as it should be and am ready for a bit of self harm. I have reinstalled/purged the installations a number of times, and even tried mariadb for something different which didn't help either. The latest error that I get is during the install of mysql-server and is listed below. I have googled for most of the day and my google-fu may have failed my but I cant seem to nut it out. The last "purge all mysql" tutorial I followed is at [http://askubuntu.com/questions/640899/uninstall-mysql-completely](http://askubuntu.com/questions/640899/uninstall-mysql-completely)

This is from the latest install:
> Setting up libevent-core-2.0-5:amd64 (2.0.21-stable-2) ...
Setting up mysql-server-core-5.7 (5.7.16-0ubuntu0.16.04.1) ...
Setting up mysql-server-5.7 (5.7.16-0ubuntu0.16.04.1) ...
update-alternatives: using /etc/mysql/mysql.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Renaming removed key_buffer and myisam-recover options (if present)
AppArmor parser error for /etc/apparmor.d/usr.sbin.mysqld in /etc/apparmor.d/usr.sbin.mysqld at line 9: Could not open 'abstractions/mysql'
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'screen-cleanup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `screen-cleanup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `screen-cleanup'
Setting up libhtml-template-perl (2.95-2) ...
Setting up mysql-server (5.7.16-0ubuntu0.16.04.1) ...

When I run a "systemctl status mysql" it says its running - see below:
>  mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: en
   Active: active (running) since Mon 2016-10-31 18:31:18 AEDT; 10min ago
 Main PID: 21302 (mysqld)
   CGroup: /system.slice/mysql.service
           &#9492;&#9472;21302 /usr/sbin/mysqld

Oct 31 18:30:48 Penelope systemd[1]: Starting MySQL Community Server...
Oct 31 18:31:18 Penelope systemd[1]: Started MySQL Community Server.
Oct 31 18:31:47 Penelope systemd[1]: Started MySQL Community Server.

However when I try to run "sudo mysql_secure_installation" or even just trying to log in I am told:
> 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)


Update: So the plot thickens. After staring at these error messages a little longer I ended up reinstalling apparmor which seems to have helped. Now the server is running and I can connect to it using "mysql -h 127.0.0.1 -u root -p" however I can not connect to it using "mysql -u root -p" or "mysql -h localhost -u root -p"? There is an entry in the hosts file for 127.0.0.1 to point to localhost but things like "mysql_secure_installation" and "mysqltuner" fail - which going by their documentation, they try to connect to "localhost".

Update 2: and got it! sorry to have bothered anyone. The solution was to create a symlink from /tmp/mysql.sock -> /var/run/mysqld/mysqld.sock using the following command.

sudo ln -s /var/run/mysqld/mysqld.sock /tmp/mysql.sock

---

### Post by PuK84 on 2016-10-31
So the plot thickens. After staring at these error messages a little longer I ended up reinstalling apparmor which seems to have helped. Now the server is running and I can connect to it using "mysql -h 127.0.0.1 -u root -p" however I can not connect to it using "mysql -u root -p" or "mysql -h localhost -u root -p"? There is an entry in the hosts file for 127.0.0.1 to point to localhost but things like "mysql_secure_installation" and "mysqltuner" fail - which going by their documentation, they try to connect to "localhost".

---

### Post by PuK84 on 2016-11-01
and got it! sorry to have bothered anyone. The solution was to create a symlink from /tmp/mysql.sock -> /var/run/mysqld/mysqld.sock using the following command.

sudo ln -s /var/run/mysqld/mysqld.sock /tmp/mysql.sock

I will mark this as solved in a moment.

---

