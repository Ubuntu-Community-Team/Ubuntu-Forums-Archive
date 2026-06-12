---
title: "Server 8.10 +Asterisk 1.6.0.9 +FreePBX 2.5.1"
date: 2009-04-20
forum: Server Platforms
---

### Post by msnyder on 2009-04-20
Hello,

I'm new to Ubuntu, I have very little knowledge of Linux from Gentoo, but I find Ubuntu nice.

I'm trying to install Asterisk 1.6.0.9 and FreePBX 2.5.1 on Unbuntu Server 8.10 but I'm having trouble. Neither is available via "apt-get", although Asterisk 1.4 is...

I have searched many sites for help, but they are not complete. Can someone point me to a step by step install, or assist me with my install from scratch? I cannot find dependaencies for Asterisk 1.6.0.9, are they the same as 1.4?

Thank you.

---

### Post by msnyder on 2009-04-20
Did I place this post in the wrong forum?

---

### Post by msnyder on 2009-04-21
Can anyone build and place packages for apt-get?

---

### Post by msnyder on 2009-04-21
I may have this licked... I've been working all day on this, but I have two problems:

1. Asterisk does not start at boot.
2. FreePBX Webpage is not password protected.

Here's how I installed:

```
INSTALL: Ubuntu Server 8.10-LAMP-OpenSSH

sudo su
nano /etc/network/interfaces
nano /etc/resolve.conf
/etc/init.d/networking restart
apt-get update
apt-get install build-essential
apt-get upgrade
adduser administrator
adduser administrator admin
apt-get install linux-headers-2.6.27-7-server php5-cli php5-mysql mysql-server php-pear php-db php5-gd curl sox libncurses5-dev libssl-dev libmysqlclient15-dev subversion
cd /usr/src
wget http://downloads.digium.com/pub/zaptel/releases/zaptel-1.4.12.1.tar.gz
wget http://downloads.digium.com/pub/libpri/releases/libpri-1.4.10.tar.gz
wget http://downloads.digium.com/pub/asterisk/releases/asterisk-1.6.0.9.tar.gz
wget http://downloads.digium.com/pub/asterisk/releases/asterisk-addons-1.6.0.1.tar.gz
wget http://downloads.digium.com/pub/asterisk/releases/asterisk-sounds-1.2.1.tar.gz
wget http://mirror.freepbx.org/freepbx-2.5.1.tar.gz
tar -xzvf zaptel-1.4.12.1.tar.gz
tar -xzvf libpri-1.4.10.tar.gz
tar -xzvf asterisk-1.6.0.9.tar.gz
tar -xzvf asterisk-addons-1.6.0.1.tar.gz
tar -xzvf asterisk-sounds-1.2.1.tar.gz
tar -xzvf freepbx-2.5.1.tar.gz
cd zaptel-1.4.12.1
./configure
make install config
cd ..
cd libpri-1.4.10
make install
cd ..
cd asterisk-1.6.0.9
./configure
make install
make samples
cd ..
cd asterisk-addons-1.6.0.1
./configure
make install
make samples
cd ..
cd asterisk-sounds-1.2.1
make install
adduser asterisk --disabled-password 
adduser www-data asterisk
cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf-orig
sed -i "s/\(^User *\)\(.*\)/\1asterisk/" /etc/apache2/apache2.conf
sed -i "s/\(^Group *\)\(.*\)/\1asterisk/" /etc/apache2/apache2.conf
/etc/init.d/apache2 restart
cd ..
cd freepbx-2.5.1
mysqladmin create asterisk
mysqladmin create asteriskcdrdb
mysql asterisk < SQL/newinstall.sql
mysql asteriskcdrdb < SQL/cdr_mysql_table.sql
mysql
GRANT ALL PRIVILEGES ON asterisk.* TO asteriskuser@localhost IDENTIFIED BY 'asteriskpassword';
GRANT ALL PRIVILEGES ON asteriskcdrdb.* TO asteriskuser@localhost IDENTIFIED BY 'asteriskpassword';
flush privileges;
quit;
asterisk
./install_amp
cp /etc/php5/apache2/php.ini /etc/php5/apache2/php.ini-orig
sed -i "s/\(upload_max_filesize *= *\)\(.*\)/\120M/" /etc/php5/apache2/php.ini
sed -i "s/\(memory_limit *= *\)\(.*\)/\1100M/" /etc/php5/apache2/php.ini
sed -i "s/\(magic_quotes_gpc *= *\)\(.*\)/\1Off/" /etc/php5/apache2/php.ini
/etc/init.d/apache2 restart
modprobe ztdummy
asterisk
amportal start
```

---

### Post by Elludium_Q-36 on 2009-04-30
No advice is better than bad advice and I see plenty of the latter...

People just throw in their senseless 2¢...

Good luck.

---

### Post by Elludium_Q-36 on 2010-03-17
I wonder how you have made out.

From what I've read, it's best to have a dedicated box if there is to ba any call volume, depending on hardware.

I'm probably going to go with LinuxMCE which installs with Kubuntu.  LinuxMCE intergrates with Media players, home automation, home security sensors/cameras, Asterisk...  [http://www.linuxmce.com/](http://www.linuxmce.com/)

AsteriskNow seems pretty good for a dedicated box:  [http://www.asterisk.org/asterisknow](http://www.asterisk.org/asterisknow)

---

