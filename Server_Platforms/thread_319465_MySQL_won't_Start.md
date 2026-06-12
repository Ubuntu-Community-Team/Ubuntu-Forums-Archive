---
title: "MySQL won't Start"
date: 2006-12-15
forum: Server Platforms
---

### Post by cknight725 on 2006-12-15
I'm following "[The Perfect Setup - Ubuntu 6.10 Server]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10")" and I cannot get MySQL to start ...

Checking /var/log/syslog and I find this:
```

mysqld[7944]: 061215 14:42:19 [ERROR] Fatal error: Can't open and lock privilege tables: Table 'mysql.host' doesn't exist
mysqld_safe[7963]: ended
/etc/init.d/mysql[8089]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
/etc/init.d/mysql[8089]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
/etc/init.d/mysql[8089]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
/etc/init.d/mysql[8089]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```

I did change the /etc/mysql/my.cnf file in two ways:
1) Commented bind to localhost line
2) Changed "datadir         = /srv/mysql_data" from default. (And because I'm a MORON, I edited the line instead of commenting old, and adding new.)

I wouldn't be surprised if the datadir change I made screwed it up, but I dunno how to fix it! Help!

---

### Post by SuperMike on 2006-12-15
Try the following at your own risk, but please review these commands carefully and make your own decision! :)

sudo /etc/init.d/mysql stop
sudo killall mysql
sudo rm -f /var/run/mysqld/mysqld.sock

...now find your database file and any configuration files you want to save and back them up.

Again, more commands to try at your own risk...

sudo apt-get --purge remove mysql-server
sudo apt-get install mysql-server
sudo /etc/init.d/mysql start

...Did you get an error? If not, then now go implementing your configuration file changes very slowly, one at a time, bouncing mysql at command line each time and seeing if you get errors. When you do, post what you were trying to do back to the forum and perhaps a MySQL guru (better than me) can help.

---

### Post by cknight725 on 2006-12-15
Fixed it!

For the record, the default for MySQL is "datadir = /var/lib/mysql".  When I commented my line, stuck this back in -- boom, MySQL started a-ok!

So what was different -- oh, nothing other than you have to copy the contents of /var/lib/mysql to whatever datadir you want to use, then make sure you chown mysql:mysql that datadir!

Copied files, changed ownership, and VOILA!

I found the important clues here: [http://www.debianadmin.com/mysql-database-server-installation-and-configuration-in-ubuntu.html](http://www.debianadmin.com/mysql-database-server-installation-and-configuration-in-ubuntu.html)
Thanks for the help!

---

### Post by shackleton on 2007-02-03
This problem comes up a number of times. Being a total newby at this, I plowed the internet endlessly and finally made it work. To be honoust I don't really know what fixed it. I followed this guide [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP), so that will be my point of referrence.

After installation, mysql worked like a charm, after reboot, it failed. Error 2002, etc. Here's what I did:
**Servername**
> Servername 127.0.0.1 in /etc/apache2/apache2.conf, I first entered the IP I get from my router, which was not the same (192.168.1.101) as
> bind-address=127.0.0.1 in /etc/mysql/my.cnf.
I figured it would probably be handy if the two were the same

**Extensions**
The instructions said:
> '$ sudo cp /usr/lib/php5/20051025/mysql.so /usr/lib/php5/ext/mysql.so' I did this for mysql.so AND for mysqli.so at first. Since I don't know what the hell it's for I decided to run the command only for mysql.so.

**Ownage**
I relocated my databasefiles as well but I didn't do that in previous attempts. I don't think it was the problem, but I was thankfull for the post above which told me to do the CHOWN thingy. 

Hopefully this is of any help to anyone.

---

