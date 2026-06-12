---
title: "&quot;Open Source Office&quot; Step by Step"
date: 2006-09-26
forum: Server Platforms
---

### Post by mikcsabee on 2006-09-26
Hello everybody!
I want to make a little Open Source Office with Ubuntu Servers and Ubuntu Clients. I made a little draw with my topology:

[IMG]http://mikcsabee.uw.hu/dokumentumok/topology.png[/IMG]

First I install the 'LDAP and NFS' server. The server IP address : 172.16.216.131.
Then I install the OpenLDAP:
```
sudo apt-get install slapd
```
And I Install the LDAP-Utils:
```
sudo apt-get install ldap-utils
```
That seems easy.

Now there comes the 'Apache and MySql' server.
I install the Ubuntu 'in LAMP  mode' (Linux Apache Mysql PHP).
This server IP is: 172.16.216.130.
I need the php5-ldap:
```
sudo apt-get install php5-ldap
```
Now need the phpLdapAdmin, so:
```
cd /var/www
wget http://superb-east.dl.sourceforge.net/sourceforge/phpldapadmin/phpldapadmin-1.0.1.tar.gz
tar -zxvf phpldapadmin-1.0.1.tar.gz
mv phpldapadmin-1.0.1 phpldapadmin
cp /var/www/phpldapadmin/config/config.php.example /var/www/phpldapadmin/config/config.php
```
Now edit the /var/www/phpldapadmin/config/config.php like this:

[IMG]http://mikcsabee.uw.hu/dokumentumok/ldap.png[/IMG]

Now we can Login to the LDAP server with phpLdapAdmin:
[http://mikcsabee.uw.hu/dokumentumok/ldap_login_1.png]("http://mikcsabee.uw.hu/dokumentumok/ldap_login_1.png")
But it seems I forgot something:
[http://mikcsabee.uw.hu/dokumentumok/ldap_login_2.png]("http://mikcsabee.uw.hu/dokumentumok/ldap_login_2.png")

Can anybody help me?
I promise when I finish I will make a big howto about this office.

---

