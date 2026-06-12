---
title: "How to change phpmyadmin username and password"
date: 2011-07-29
forum: Server Platforms
---

### Post by dmubu on 2011-07-29
Hello,

I have recently installed phpmyadmin and have logged in successfully.  However, my default username is 'root'.  I want to change that username to something else.

I ran the following command:
```
 mysql -u foo -p
```
I received this error: 
```
Access denied for user 'foo'@'localhost' (using password: YES)
```
Is there a certain configuration file I have to edit?  If so, which one?

Thank you so much!

---

### Post by Habitual on 2011-07-29
have you give 'foo' a db permission to connect to a db?

also, in case the actual was sanitized, try this:
```
mysql -h localhost -u root -p
```
enter the root password and let us know.

Have you modified the my.cnf in any way?
Is the mysql server process/service started?

---

### Post by dmubu on 2011-07-29
Thanks for the reply..

My issue has changed slightly.  I removed the LAMP stack and re-installed.

Apache and PHP work fine, but I have two main problems:

1) MySQL server is not working properly.  When I enter (with password):

```
sudo mysql -u root -p
```

I receive:

```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```

2) I cannot install phpMyAdmin properly.  After running sudo apt-get install phpmyadmin, I receive.

```


 The phpmyadmin package must have a database installed and configured      
 &#9474; before it can be used.  This can be optionally handled with              
 &#9474; dbconfig-common.                                                          
 &#9474;                                                                           
 &#9474; If you are an advanced database administrator and know that you want to   
 &#9474; perform this configuration manually, or if your database has already      
 &#9474; been installed and configured, you should refuse this option.  Details     
 &#9474; on what needs to be done should most likely be provided in                 
 &#9474; /usr/share/doc/phpmyadmin.                                                
 &#9474;                                                                            
 &#9474; Otherwise, you should probably choose this option.             


```

I clicked 'OK' and selected the option to configure with apache.  However, it seems that, since MySQL server is not configured properly, phpmyadmin will not install.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  phpmyadmin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/4,321 kB of archives.
After this operation, 17.8 MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package phpmyadmin.
(Reading database ... 166419 files and directories currently installed.)
Unpacking phpmyadmin (from .../phpmyadmin_4%3a3.3.10-1_all.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up phpmyadmin (4:3.3.10-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf

Creating config file /etc/dbconfig-common/phpmyadmin.conf with new version

Creating config file /etc/phpmyadmin/config-db.php with new version
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES).
unable to connect to mysql server.
error encountered creating user:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
dbconfig-common: phpmyadmin configure: ignoring errors from here forwards
populating database via sql...  done.
dbconfig-common: flushing administrative password




```

Thus, I can access neither MySQL server nor phpMyAdmin.  What can I do?

Thank you.

---

### Post by Habitual on 2011-07-29
You don't know or remember your mysql root password?

I suggested
```
mysql -h localhost -u root -p
```
and you typed something else. :(

```
pidof mysqld
``` says what exactly? If nothing then
```
sudo service mysql start
``` and try
```
mysql -h localhost -u root -p
``` again.


Re-configure mysql-server:
```
sudo dpkg-reconfigure mysql-server
```
or 
```
sudo dpkg-reconfigure mysql-server-5.1
```

whichever one is installed.


Once you reconfigure (and recover) your root mysql password, then
Reconfigure *phpmyadmin*
```
sudo dpkg-reconfigure phpmyadmin
```

---

### Post by dmubu on 2011-07-29
Thanks for the quick reply.  I apologize for not following earlier instructions.

This is what I have done.

```

sudo dpkg-reconfigure mysql-server-5.1
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
mysql start/running, process 7598

```

Next, I tried:
```

sudo dpkg-reconfigure phpmyadmin

```

I followed the prompts to:
1) reinstall the database
2) uses unix socket connection method
3) entered 'root' for name of database's administrative user
4) entered password for database's administrative user
5) entered name of database
6) chose to reconfigure with apache2

I then received:
```

An error occurred while installing the database:                            
 &#9474;                                                                             
 &#9474; ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using        
 &#9474; password: YES)                                                              
 &#9474;                                                                             
 &#9474; If at this point you choose "retry", you will be prompted with all the      
 &#9474; configuration questions once more and another attempt will be made at       
 &#9474; performing the operation. "retry (skip questions)" will immediately         
 &#9474; attempt the operation again, skipping all questions.  If you choose         
 &#9474; "abort", the operation will fail and you will need to downgrade,            
 &#9474; reinstall, reconfigure this package, or otherwise manually intervene to     
 &#9474; continue using it.  If you choose "ignore", the operation will continue, 


```

What should I do?

---

### Post by dmubu on 2011-07-30
I was able to access MySQL server using the help of this link:

[http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html)

---

