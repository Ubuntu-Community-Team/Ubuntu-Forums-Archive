---
title: "PostgreSQL and PHP"
date: 2010-04-21
forum: Server Platforms
---

### Post by knowram on 2010-04-21
I have installed a LAMP server with webmin on top of it and then installed PostgreSQL. however i don't seem to be able to connect to my PostgreSQL databases using php. It's looking like the PostgreSQL module isn't configured within php however i am unable to figure out how to do that. can someone help me out?

Thanks

---

### Post by sh1ny on 2010-04-21
Describe please how did you install postgresql. Did you configure users for it ? Did you install php5-pgsql package and restart apache2 after that ?

---

### Post by knowram on 2010-04-21
I installed postgresql through webmin and i have configured users. I don't think i have installed the php5-pgsql package. after your post thought i did a search for the download and i found this [http://packages.ubuntu.com/jaunty/php5-pgsql](http://packages.ubuntu.com/jaunty/php5-pgsql) however when i tried to install it I got this error ```
root@ar01:/home/knowram# dpkg -i php5-pgsql_5.2.6.dfsg.1-3ubuntu4.5_i386.deb 
Selecting previously deselected package php5-pgsql.
(Reading database ... 71356 files and directories currently installed.)
Unpacking php5-pgsql (from php5-pgsql_5.2.6.dfsg.1-3ubuntu4.5_i386.deb) ...
dpkg: dependency problems prevent configuration of php5-pgsql:
 php5-pgsql depends on php5-common (= 5.2.6.dfsg.1-3ubuntu4.5); however:
  Version of php5-common on system is 5.2.10.dfsg.1-2ubuntu6.
dpkg: error processing php5-pgsql (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 php5-pgsql

```

I am running php 5.2.10-2ubuntu6 could that be the problem? if so can someone help me find the right package download?

---

### Post by ICEB3AR on 2010-04-21
What about simply:
```
sudo apt-get install php5-pgsql
sudo /etc/init.d/apache2 restart
```

---

