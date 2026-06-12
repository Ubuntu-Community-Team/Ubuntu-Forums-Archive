---
title: "Simple MySQL Question"
date: 2005-01-08
forum: Server Platforms
---

### Post by deception on 2005-01-08
I've installed Apache2, Php4 and MySQL. Is there a default password for the DB or a place I can set one please? 

I've tried reading the MySQL docs @ the official site, but I just got perplexed and gave up  8-[   =D> 

Any help appreciated,
Matt

---

### Post by deception on 2005-01-08
BTW i've tried /usr/local/mysql/bin/msql -u root and it says no such file or directory  :sad: I installed through apt-get. Following Ubuntuguide.org

EDIT: [b]I've found the MySQL config file. I've set the password and username and when loging in with phpmyadmin i get this error: 

 	

#2002 - Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


[/b]

Any ideas? Many thanks.

---

### Post by cpinto on 2005-01-08
[QUOTE=deception]BTW i've tried /usr/local/mysql/bin/msql -u root and it says no such file or directory  :sad: I installed through apt-get. Following Ubuntuguide.org

EDIT: [b]I've found the MySQL config file. I've set the password and username and when loging in with phpmyadmin i get this error: 

 	

#2002 - Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


[/b]

Any ideas? Many thanks.[/QUOTE]
 Do this:
/usr/bin/mysqladmin -u root password 'yourpasswordhere'

and you should be able to login after that (as root).

---

### Post by zeroK on 2005-01-09
[QUOTE=deception]BTW i've tried /usr/local/mysql/bin/msql -u root and it says no such file or directory  :sad: I installed through apt-get. Following Ubuntuguide.org

EDIT: [b]I've found the MySQL config file. I've set the password and username and when loging in with phpmyadmin i get this error: 

 	

#2002 - Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


[/b]

Any ideas? Many thanks.[/QUOTE]
 Are you sure that the database server is running? You should be able to start it with /etc/init.d/mysqld start

---

