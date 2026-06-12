---
title: "I can't seem to connect to mysql"
date: 2011-07-24
forum: Server Platforms
---

### Post by Fertech on 2011-07-24
I'm using ubuntu 10.04 LTS I install mysql

```
sudo apt-get install mysql-server

```

I set up my password and confirm

I type mysql at the terminal and i get this back.

```
 gorda@Fertech-Mendoza:~$ mysql
Warning: World-writable config file '/etc/mysql/my.cnf' is ignored
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
gorda@Fertech-Mendoza:~$ 
 
```  
 
how can I correct this issue.

---

### Post by brighty22 on 2011-07-24
The first line is a permissions error. MySQL is complaining its config file is too open - fix it with

```
sudo chmod 0644 /etc/mysql/my.cnf
```

Next I'd give mysql a restart - sometimes the second error is caused by the service not actually running, or as a result of the first error:

```
sudo service mysql restart
```

If you get a message about mysql not currently running, replace 'restart' with 'start' in the command above, then try connecting with

```
mysql -u root -p
```

---

### Post by Madjid-9-3 on 2011-11-29
Thanks a lot, it solves my problem.:smile:

---

