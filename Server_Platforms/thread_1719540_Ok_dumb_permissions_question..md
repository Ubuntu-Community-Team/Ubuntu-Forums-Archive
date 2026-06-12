---
title: "Ok dumb permissions question."
date: 2011-04-01
forum: Server Platforms
---

### Post by untenops on 2011-04-01
I have a ubuntu server setup, 10.04. And One of its functions is to allow other computer on my LAN to backup to it.  For example my wifes laptop running vista, backs up using alwaysync, to a folder I created for her on the ubuntu server.  But in order to get this to work I had to open up her folder to rwxrwxrwx.  Now its available to anyone and everyone on the network.  Not to big of a deal, it on my LAN, in my house and her and I are the only ones with access.  If there is a better way to do this please let me know.  Now I want to do the same for my desktop, but since I'm using ubuntu for my desktop as well, I don't think I would need to open my folder to everyone as well.  Both the server and my desktop use the same user name for the admin accounts.  But for some reason I still do not have access.  What do I need to do?  Thanks.

---

### Post by Ryan Dwyer on 2011-04-02
Are you using samba? If so, read the Samba docs and configure it so the client must authenticate to be able to write to the share.

---

### Post by usatonycuba on 2011-04-05
Do you know how to work Mysql Server and FTP Server? .. you can set these servers and provide access from your LAN only, or via web if you want too.. is a safe and easy .. I believe

---

### Post by untenops on 2011-04-05
> **usatonycuba said:**
> Do you know how to work Mysql Server and FTP Server? .. you can set these servers and provide access from your LAN only, or via web if you want too.. is a safe and easy .. I believe

Would you happen to have any suggestions, or links showing how to do this?  My server has the lamp installation so MySQL is there, but I don't know much bout it, but would love to learn. :D

As for samba, yes its installed, and I do need to learn more about its setup.  More Googling and readings for me.

---

### Post by usatonycuba on 2011-04-06
Easy way to use a FTP- MYSQl base (for files store) is to install, pure-ftpd-mysql base...(This installation has no guarantees and I do not take responsibility for any damage that may cause)
I've used in previous installations and should not cause problems .. but as I mention .. is completely up to you....

FTP- MYSQl base
```
apt-get install pure-ftpd-mysql
```to add a new ftp group named "2012"...Run
```
groupadd -g 2012 ftpgroup
```to add a new user named "2012" with bin set to false and null ("without any valid shell", and "including ftp virtual users") Run
```
useradd -u 2012 -s /bin/false -d /bin/null -c "pureftpd user" -g  ftpgroup ftpuser
```to create pureftpd database ...Run
```
mysql -u root -p
```then copy/paste this... change (IDENTIFIED BY 'your pass goes here').. for you desire own pass


```

CREATE DATABASE pureftpd;
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP ON pureftpd.* TO  'pureftpd'@'localhost' IDENTIFIED BY 'your pass goes here';
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP ON pureftpd.* TO  'pureftpd'@'localhost.localdomain' IDENTIFIED BY 'your pass goes here';
FLUSH PRIVILEGES;

```..and... USE pureftpd .. Run this
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

```Do not forget to copy (backup) the original file... and do this.. Run
```

cp /etc/pure-ftpd/db/mysql.conf /etc/pure-ftpd/db/mysql.conf_orig
cat /dev/null > /etc/pure-ftpd/db/mysql.conf

```Edit your mysql.conf
```

nano /etc/pure-ftpd/db/mysql.conf

```your mysql.conf, It should like this:

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

```Make sure to replace the string ftpdpass with the real password for the MySQL user pureftpd in the line MYSQLPassword! Please note that we use md5 as MYSQLCrypt method, which means we will store the users&#8217; passwords as an MD5 string in the database which is far more secure than using plain text passwords!

Then you should Create the files >> /etc/pure-ftpd/conf/ChrootEveryone, >>  /etc/pure-ftpd/conf/CreateHomeDir ..and... >>  /etc/pure-ftpd/conf/DontResolve ... ( all which simply contains the string "yes" ):
```

echo "yes" > /etc/pure-ftpd/conf/ChrootEveryone
echo "yes" > /etc/pure-ftpd/conf/CreateHomeDir
echo "yes" > /etc/pure-ftpd/conf/DontResolve

```Restart PureFTPd
```

/etc/init.d/pure-ftpd-mysql restart

```we have installed Pure-ftpd mysql based, create an option that users have their own folder .. what remains is to create users in your database (manually if want to) .. directly you can do in phpmyadmin ... Open [http://localhost/phpmyadmin](http://localhost/phpmyadmin) , select  pureftpd DATABASE, click on SQL to Run SQL query/queries on server "localhost", and  then you can created a new FTP user with:

```

INSERT INTO `ftpd` (`User`, `status`, `Password`, `Uid`, `Gid`, `Dir`, `ULBandwidth`, `DLBandwidth`, `comment`, `ipaccess`, `QuotaSize`, `QuotaFiles`) VALUES ('user_name_goes_here', '1', MD5('user_pass_goes_here'), '2012', '2012', '/home/user_name_goes_here', '100', '100', '', '*', '50', '0');

```let's break down that information:

`User` =the uer name of the account
`status` = if (active user) have to set to 1,  not active have to set to (cero) 0
`Password` = pass of the user account
`Uid` = (system  ftp-user that we created earlier) named "2012"
`Gid` = (system  ftp-group that we created earlier) named "2012"
`Dir` =where will be the user dir for his/her ftp-files that will be store in your system
`ULBandwidth` = Upload  Bandwidth that user will be able to use
`DLBandwidth` = Download  Bandwidth that user will be able to use
`comment` = Leave blank
`ipaccess` = You can Leave blank for ANY IP, or give the specific IP where the user will be able to connect from (if specific IP is set, they have to use JUST that one mandatory)
`QuotaSize` = size of the space (of the total store) that user will be allow to use for that account
`QuotaFiles` = cero will be ok

Now you can use a web based FTP client like net2ftp ( [www.net2ftp.com/]("http://www.net2ftp.com/") ) to test your ftp.. (is recommended to use >> Connecting*Passive mode, FTP mode*Automatic, port*21, for the FTP server* use your own ip if you don't have FQDN.... net2ftp also have the option to download and use in your apache server.

---

