---
title: "pureftpd.org"
date: 2011-04-02
forum: Server Platforms
---

### Post by evarie on 2011-04-02
Please help me to understand this file: [http://download.pureftpd.org/pub/pure-ftpd/doc/README](http://download.pureftpd.org/pub/pure-ftpd/doc/README)

        ------------------------ COMPILATION ------------------------
 * Step 1 (optional but recommended):


question 1:
Create a specific, unprivileged user and group called _pure-ftpd, without any valid
shell. Don't use this for anything else, including FTP virtual users.

What means "without any valid shell" ?

What means "including ftp virtual users" ?



question 2:
useradd -g _pure-ftpd -d /var/empty -s /etc _pure-ftpd

What means this useradd with their switches?
And what will happen if i command this on my ubuntu server?


question 3:
If having a user whose name begins with an underscore is a no-go for you, you can
also call it pure-ftpd, without the underscore.

What means "an underscore is a no-go for you" ?

* Step 2:

question 4:
If you have Cdialog or Xdialog installed on your system, try the following command
to build and install Pure-FTPd:

What is a Cdialog and what is a Xdialog?

question 5:
make -f Makefile.gui

what will happen if i command this on my ubuntu server?

question 6:
If you don't have Cdialog or if you prefer the conventional way, here it is:

./configure
make install-strip

Et voila! The software is now installed in /usr/local/sbin/pure-ftpd

What means "make install-strip" ?




This is my real love for ubuntu server with ftpd.
Thanks a lot at all !

---

### Post by evarie on 2011-04-02
I did ask the mailing list of pureftpd.
This is de answer: [six questions with answer from the list]("http://archives.pureftpd.org/archives.cgi?100:mss:3992:ofmkakpgpcpobpikojfk")

Can you add more information (here in this forum thread) for humans who start a pureftpd server with ubuntu server?

---

### Post by usatonycuba on 2011-04-05
Easy way, is to use pure-ftpd-mysql base...
```
apt-get install pure-ftpd-mysql
```
to add a new ftp group named "2012"...Run 
```
groupadd -g 2012 ftpgroup
```to add a new user named "2012" with bin set to false and null ("without any valid shell", and  "including ftp virtual users") Run 
```
useradd -u 2012 -s /bin/false -d /bin/null -c "pureftpd user" -g  ftpgroup ftpuser
```to create pureftpd database ...Run
```
mysql -u root -p
```then copy/paste this...


```

CREATE DATABASE pureftpd;
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP ON pureftpd.* TO  'pureftpd'@'localhost' IDENTIFIED BY 'your pass goes here';
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP ON pureftpd.* TO  'pureftpd'@'localhost.localdomain' IDENTIFIED BY 'your pass goes here';
FLUSH PRIVILEGES;

```..and... pureftpd user.. Run
```

USE pureftpd;

```then copy/paste this...

```

CREATE TABLE ftpd (
User varchar(16) NOT NULL DEFAULT '',
STATUS enum('0','1') NOT NULL DEFAULT '0',
Password varchar(64) NOT NULL DEFAULT '',
Uid varchar(11) NOT NULL DEFAULT '-1',
Gid varchar(11) NOT NULL DEFAULT '-1',
Dir varchar(128) NOT NULL DEFAULT '',
ULBandwidth smallint(5) NOT NULL DEFAULT '0',
DLBandwidth smallint(5) NOT NULL DEFAULT '0',
comment tinytext NOT NULL,
ipaccess varchar(15) NOT NULL DEFAULT '*',
QuotaSize smallint(5) NOT NULL DEFAULT '0',
QuotaFiles int(11) NOT NULL DEFAULT 0,
UNIQUE KEY User (User)
) TYPE=MyISAM;

quit;

```Don you forget to copy (backup) the original file... and do this.. Run
```

cp /etc/pure-ftpd/db/mysql.conf /etc/pure-ftpd/db/mysql.conf_orig
cat /dev/null > /etc/pure-ftpd/db/mysql.conf

```Edit your mysql.conf
```

nano /etc/pure-ftpd/db/mysql.conf

```
your mysql.conf, It should like this:

```

MYSQLSocket      /var/run/mysqld/mysqld.sock
#MYSQLServer     localhost
#MYSQLPort       3306
MYSQLUser       pureftpd
MYSQLPassword   your pass goes here
MYSQLDatabase   pureftpd
#MYSQLCrypt md5, cleartext, crypt() or password() - md5 is VERY RECOMMENDABLE uppon cleartext
MYSQLCrypt      md5
MYSQLGetPW      SELECT Password FROM ftpd WHERE User="\L" AND status="1" AND (ipaccess = "*" OR ipaccess LIKE "\R")
MYSQLGetUID     SELECT Uid FROM ftpd WHERE User="\L" AND status="1" AND (ipaccess = "*" OR ipaccess LIKE "\R")
MYSQLGetGID     SELECT Gid FROM ftpd WHERE User="\L"AND status="1" AND (ipaccess = "*" OR ipaccess LIKE "\R")
MYSQLGetDir     SELECT Dir FROM ftpd WHERE User="\L"AND status="1" AND (ipaccess = "*" OR ipaccess LIKE "\R")
MySQLGetBandwidthUL SELECT ULBandwidth FROM ftpd WHERE User="\L"AND status="1" AND (ipaccess = "*" OR ipaccess LIKE "\R")
MySQLGetBandwidthDL SELECT DLBandwidth FROM ftpd WHERE User="\L"AND status="1" AND (ipaccess = "*" OR ipaccess LIKE "\R")
MySQLGetQTASZ   SELECT QuotaSize FROM ftpd WHERE User="\L"AND status="1" AND (ipaccess = "*" OR ipaccess LIKE "\R")
MySQLGetQTAFS   SELECT QuotaFiles FROM ftpd WHERE User="\L"AND status="1" AND (ipaccess = "*" OR ipaccess LIKE "\R")

```Make sure to replace the string ftpdpass with the real password for the MySQL user pureftpd in the line MYSQLPassword! Please note that we use md5 as MYSQLCrypt method, which means we will store the users’ passwords as an MD5 string in the database which is far more secure than using plain text passwords!

Then you should Create the file /etc/pure-ftpd/conf/ChrootEveryone, /etc/pure-ftpd/conf/CreateHomeDir ..and...  /etc/pure-ftpd/conf/DontResolve ...all which simply contains the string yes:
```

echo "yes" > /etc/pure-ftpd/conf/ChrootEveryone
echo "yes" > /etc/pure-ftpd/conf/CreateHomeDir 
echo "yes" > /etc/pure-ftpd/conf/DontResolve 

```Restart PureFTPd
```

/etc/init.d/pure-ftpd-mysql restart

```You should by ok from there

---

