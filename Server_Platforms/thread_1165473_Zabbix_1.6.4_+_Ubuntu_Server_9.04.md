---
title: "Zabbix 1.6.4 + Ubuntu Server 9.04"
date: 2009-05-20
forum: Server Platforms
---

### Post by rauldinho on 2009-05-20
Hi, recently at work they asked me to implement a network monitoring software. I will try using zabbix. I've been reading the official manual and searching the forum and the web, but i wanted to know if someone could give me something proven and bug free, since i don't have too much time for testing because people want it in production soon *just my luck :(* Anyway i'll continue trying, but any help i would deeply appreciate it. Thanks in advanced!

---

### Post by freakscene on 2009-05-21
cacti, nagios, and mrtg could be other options and all work very well and are very reliable for me.

i just tried a zabbix install on jaunty. the server and agent installed fine, and the database is set up. all the services are running, but i can not find anywhere within the documentation on what the default index page is, or where to find it, so i can begin configuring.

i have an old zabbix install set up on another *nix box and it works very well, but it actually installs a /home/zabbix directory which is where the public_html page is located.

anyone have any ideas?

the zabbix manual instructs you to point your browser to the zabbix URL but doesnt tell you what it is !

thanks
- fs

---

### Post by freakscene on 2009-05-21
i found the step by step

[http://www.zabbix.com/wiki/doku.php?id=howto:ubuntuinstall](http://www.zabbix.com/wiki/doku.php?id=howto:ubuntuinstall)

good luck!

---

### Post by wickeda on 2009-05-27
Here's a howto for Ubuntu 8.04 - should be the same on 9.04:


-------------------------------------------------------------------------
Howto: Installation of Zabbix 1.6.4 on Ubuntu 8.04 Hardy Heron
-------------------------------------------------------------------------

Needed Components:
 - Apache
 - MySQL-Server
 - PHP5

1. Installation of needed packages:
sudo aptitude install build make snmp libsnmp-dev php5-gd snmpd libmysql++-dev


2. Make the zabbix user and group:
sudo adduser zabbix
sudo adduser zabbix admin
su - zabbix


3. Download and extract the source:
wget "http://switch.dl.sourceforge.net/sourceforge/zabbix/zabbix-1.6.4.tar.gz"
tar zxvpf zabbix-1.6.4.tar.gz


4. Create a zabbix database and populate it:
mysql -u root -p
create database zabbix;
quit;

mysql -u root -p zabbix < /home/zabbix/zabbix-1.6.4/create/schema/mysql.sql
mysql -u root -p zabbix < /home/zabbix/zabbix-1.6.4/create/data/data.sql


5 - Configure, compile and install the server:
cd zabbix-1.6.4/
./configure --prefix=/usr --with-mysql --with-net-snmp --enable-server --enable-agent
make
sudo make install


6 - Prepare the rest of the system:

sudo nano /etc/services
     Add at the end:
         zabbix_agent 10050/tcp # Zabbix ports
         zabbix_trap 10051/tcp
     Save and exit.

sudo mkdir /etc/zabbix
sudo chown -R zabbix.zabbix /etc/zabbix/
cp misc/conf/zabbix_* /etc/zabbix

nano /etc/zabbix/zabbix_server.conf
     Change the SQL-Password:
            # Database password
            # Comment this line if no password used
            DBPassword=<password>
     Save and exit.

sudo zabbix_server
sudo zabbix_agent


7 - Configure web interface:

mkdir /home/zabbix/public_html
cp -R /home/zabbix/zabbix-1.6.4/frontends/php/* /home/zabbix/public_html/

Edit /etc/apache2/sites-enabled/000-default:
     sudo nano /etc/apache2/sites-enabled/000-default
Work into file:
     Alias /zabbix/ /home/zabbix/public_html/
     <Directory /home/zabbix/public_html>
          AllowOverride FileInfo AuthConfig Limit Indexes
          Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
     <Limit GET POST OPTIONS PROPFIND>
          Order allow,deny
          Allow from all
     </Limit>
     <LimitExcept GET POST OPTIONS PROPFIND>
          Order deny,allow
          Deny from all
     </LimitExcept>
     </Directory>
Save and exit.

sudo nano /etc/php5/apache2/php.ini
     Change the following values:
            max_execution_time = 300 ; Maximum execution time of each script, in seconds
            date.timezone = Europe/Berlin
     Save and exit.

sudo /etc/init.d/apache2 restart


8. Final Steps:
Point your browser to: http://<servername or ip>/zabbix/

- Introduction: read and click Next
- License Agreement: Read, check 'I Agree', click Next
- Check of Pre-Requisites: Fix any problems, click retry. Click Next when all pre-requisites are OK.
- Configure DB Connection: Enter appropriate settings and click Test Connection.
- Click Next when OK.
- Pre-Installation Summary: Verify installation settings, click Next.
- Install: Click Save Configuration file and save to machine.
  Copy zabbix.conf.php to /home/zabbix/public_html/conf/zabbix.conf.php
  One way to do this from a desktop machine (requires ssh installed):
  scp zabbix.conf.php zabbix@<serverip>:/home/zabbix/public_html/conf/
- Click Retry and click Next when OK.
- Finish: Click Finish to complete installation.

---

