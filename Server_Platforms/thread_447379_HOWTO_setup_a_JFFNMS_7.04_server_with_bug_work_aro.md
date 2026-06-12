---
title: "HOWTO setup a JFFNMS 7.04 server with bug work around too"
date: 2007-05-17
forum: Server Platforms
---

### Post by jaakan on 2007-05-17
Note there is a bug in Package: jffnms (0.8.3dfsg.1-2) [universe]
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=419551](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=419551)

Clean install of 7.04 server
or 6.06 upgraded to 7.04 server
or 6.10 upgraded to 7.04 server


sudo vi /etc/apt/sources.list ( enable the other repos )
sudo aptitude update
sudo aptitude dist-upgrade

sudo aptitude install openssh-server clamav clamav-daemon apache2 php5 snmpd snmp graphviz tftpd ntp nmap fping mysql-server dbconfig-common libapache2-mod-php5 php-pear php5-cli php5-gd php5-mysql php5-snmp rrdtool ntp tac-plus ttf-bitstream-vera mtop htop


sudo mysqladmin password xxxxx ( set a password ) ie: "mysql" 

if you don't you will need to do this before installing jffnms

	type "mysql -u root"
	mysql> CREATE DATABASE jffnms;
	mysql> GRANT ALL PRIVILEGES ON jffnms.* TO jffnms@localhost IDENTIFIED BY 'jffnms';
	mysql> FLUSH PRIVILEGES;
	mysql> quit

set theses options in your Apache2's php.ini
sudo vi /etc/php5/apache2/php.ini
register_globals = On

sudo aptitude install jffnms
sudo ln -s /usr/share/jffnms/htdocs /var/www/jffnms
sudo ln -s /var/lib/jffnms/tempimages  /usr/share/jffnms/htdocs/images/temp

sudo chmod 775 /usr/share/jffnms/htdocs
sudo chmod 777 /usr/share/jffnms/conf
sudo chmod 777 /var/lib/jffnms/tempengine 
sudo chmod 777 /var/lib/jffnms/tempimages

sudo vi /usr/share/jffnms/conf/jffnms.conf.defaults 

change jffnms_real_path:default = /opt/jffnms to /usr/share/jffnms/

sudo apt-get upgrade
and reboot and it should be up and running

[http://server/jffnms](http://server/jffnms) you'll get the setup page 
save and reboot for to be sure

[http://server/jffnms](http://server/jffnms)
login as admin / admin

---

