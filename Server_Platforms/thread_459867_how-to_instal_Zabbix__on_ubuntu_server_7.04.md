---
title: "how-to instal Zabbix  on ubuntu server 7.04"
date: 2007-05-31
forum: Server Platforms
---

### Post by TommeN on 2007-05-31
Hello,

I'm trying to install Zabbix on Ubuntu server 7.04, but that is not quite easy that i thought.
Anyone have a good tut for that? i've been trying this tut: [http://www.subvs.co.uk/server_monitoring_ubuntu_zabbix](http://www.subvs.co.uk/server_monitoring_ubuntu_zabbix)

But when i did the ./configure i just get a message that i dont have any "c compiler". How do i install the correct c compiler?

Thanks in advance.
---TommeN

---

### Post by craigp84 on 2007-05-31
Hi TommeN,

To get a sane, but basic, build environment, ubuntu includes a handy meta-package which depends on the relevant tools. Just enter the following at a command line and it'll sort you out with the crtical stuff:

```
sudo apt-get install build-essential
```

As for the docs, if there's no others around, make sure you take notes and post your process on the wiki. Others can then refine what you wrote over time to reflect their experiences too.

Otherwise the next person gets the same problem as you :-(

Hope this helps,

-c

---

### Post by TommeN on 2007-05-31
when i do a "./configure  --enable-server --enable-agent --with-mysql --with-net-snmp" this message appared in the end:

```
checking for mysql_config... no
configure: error: Not found MySQL library
```

i have mysql installed.. So what is the problem?

---

### Post by TommeN on 2007-05-31
I fixed the problem in the post over. But now i got a new one.
Under the same ./config i get this message:

checking for net-snmp-config... no
configure: error: Invalid NET-SNMP directory - unable to find net-snmp-config


Then it stops again... I have installed the package: "snmp" but that didnt help...

---

### Post by jose_ramirez on 2007-06-12
> **TommeN said:**
> I fixed the problem in the post over. But now i got a new one.
Under the same ./config i get this message:

checking for net-snmp-config... no
configure: error: Invalid NET-SNMP directory - unable to find net-snmp-config


Then it stops again... I have installed the package: "snmp" but that didnt help...

Can you share what you did to fix the mysql problem?

Thanks.

---

### Post by selectron on 2007-06-14
Hi!
TommeN, I had this problem with net-snmp. I think you must install libsnmp9-dev package.
Hope that it will help.
Sorry for my English.

---

### Post by bkingx on 2007-06-20
Hi all!  I had the same problems.  I just finished a good install on feisty and my steps are below:


Intended for Zabbix 1.4 on Ubuntu Feisty Fawn 7.04


Install pre-requisites:
Apache
MySQL-Server
PHP5
Net-Snmp libraries

sudo aptitude install build-essentials mysql-server php5 php5-gd snmp libsnmp9-dev snmpd

1 - Make the zabbix user and group:

sudo adduser zabbix
	enter in new password
	confirm
	use the remaining defaults.

Add zabbix to the admin group:

sudo adduser zabbix admin


2 - Download and Untar the sources:

su - zabbix
wget [http://internap.dl.sourceforge.net/sourceforge/zabbix/zabbix-1.4.tar.gz](http://internap.dl.sourceforge.net/sourceforge/zabbix/zabbix-1.4.tar.gz)
tar zxvpf zabbix-1.4.tar.gz


3 - Create a zabbix database and populate it:

mysql -u root -p
create database zabbix;
quit;

mysql -u root -p zabbix < /home/zabbix/zabbix-1.4/create/schema/mysql.sql
mysql -u root -p zabbix < /home/zabbix/zabbix-1.4/create/data/data.sql


4 - Configure, compile and install the server:

cd zabbix-1.4/
./configure --prefix=/usr --with-mysql --with-net-snmp \
--enable-server --enable-agent &&
make
sudo make install


5 - Prepare the rest of the system:

sudo nano /etc/services

Add at the end:

zabbix_agent 10050/tcp # Zabbix ports
zabbix_trap 10051/tcp

Save and exit.

sudo mkdir /etc/zabbix
sudo chown -R zabbix.zabbix /etc/zabbix/
cp misc/conf/zabbix_* /etc/zabbix/

Edit /etc/zabbix/zabbix_agentd.conf:

nano /etc/zabbix/zabbix_agentd.conf

Make sure that the Server parameter points to the server address, for the agent that runs on the server it is like this:

Server=127.0.0.1

Edit /etc/zabbix/zabbix_server.conf:

nano /etc/zabbix/zabbix_server.conf

For small sites this default file will do, however if you are into tweaking your config for your 10+ hosts site, this is the place.

Change this:

# Database password
# Comment this line if no password used

DBPassword=Secret

Start the server :

zabbix_server

Start the client:

zabbix_agentd &


6 - Configure web interface

mkdir /home/zabbix/public_html
cp -R frontends/php/* /home/zabbix/public_html/

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

Make php.ini adjustments:

sudo nano /etc/php5/apache2/php.ini

Change the following values:

max_execution_time = 300     ; Maximum execution time of each script, in seconds
date.timezone = America/Kentucky/Louisville
(use this url to find your correct timezone format: [http://us3.php.net/manual/en/timezones.php](http://us3.php.net/manual/en/timezones.php) )


Restart Apache:

sudo /etc/init.d/apache2 restart


Now point your browser to:

http://<servername or ip>/zabbix/

1. Introduction

read and click Next

2. License Agreement

Read, check 'I Agree', click Next

3. Check of Pre-Requisites

Fix any problems, click retry.  Click Next when all pre-requisites are OK.

4. Configure DB Connection

Enter appropriate settings and click Test Connection.
Click Next when OK.

5. Pre-Installation Summary

Verify installation settings, click Next.

6. Install

Click Save Configuration file and save to machine.
Copy zabbix.conf.php to /home/zabbix/public_html/conf/zabbix.conf.php

One way to do this from a desktop machine (requires ssh installed):
scp zabbix.conf.php zabbix@<serverip>:/home/zabbix/public_html/conf/

Click Retry and click Next when OK.

7. Finish

Click Finish to complete installation.


Your New Zabbix install will now be shown.

Log in with username: Admin
No Password

First go to the tab Configuration and then Hosts.

Now create a host-group, see that you can give it some templates, e.g: Application.MySQL, Host.SNMP, Host.Standalone, Host.Unix.

Then some hosts:

Select your host-group and use Link with Template Host.Unix

Now a lot of triggers are imported and the game begins.

Go to the monitoring tab and watch the latest values roll in.

For specifics on configuration, please refer to the Zabbix user manual.

[www.zabbix.com](www.zabbix.com)

---

### Post by surlyjake on 2007-07-03
WORKED!!!

thanks bkingx.
actually followed this for an install on Debian etch. 

zabbix 1.4 is fantastic. if doing a fresh install dont waste time with 1.1.4 from repositories.

three beers to you, bkingx.

---

### Post by aksuda on 2007-07-23
> **jose_ramirez said:**
> Can you share what you did to fix the mysql problem?

Thanks.

I had the same problem. The fix was to install **libmysqlclient15-dev**

---

### Post by honeydew on 2007-11-26
this worked for me as well.. thanks for the howto

---

### Post by tanveer on 2007-12-27
:guitar: WOW. Thanks a lot. It saved the day dude..bkingx u r gr8.
thanks for this great howto.

---

