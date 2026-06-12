---
title: "Upgrade from 16.04 LTS to 18.04.1 LTS - MySQL server problem"
date: 2021-08-26
forum: Server Platforms
---

### Post by synsteph38 on 2021-08-26
Hello,

I've made an upgrade form 16.04 to 18.04.1 without apparently any problem (hosted on a 1&1 dedicated server)
This server is running different Joomla! based sites
Had to restart MySQL server and then no more any response form MySQL server

Have tried re-installation with :
```
sudo apt-get remove mysql-server
sudo apt-get install mysql-server
```

Without any luck (ie none of our sites are running now)
Tried to stop and start MySQL server : no problem

Tried re-configuration with :
```
sudo dpkg-reconfigure mysql-server-5.7
```
Got this message after re-configuration :
```
Checking if update is needed.
This installation of MySQL is already upgraded to 5.7.35, use --force if you still need to run mysql_upgrade
```

Didn't help either... I'm not that familiar with MySQL server (have installed it many times, never had any problem... used it without any problem)
But now I'm lost  :( !

has someone an idea what I should do ?
Should I give you more information, fell free to ask (please dive me the bash command to enter, I'm not that fluent in Bash ;)) ? 

Thanks in advance for your help and advises,

Stéphane

PS : please forgive me my English as it is not my mother language, I am French

---

### Post by synsteph38 on 2021-08-26
Forgot to say 

```
/var/lib/mysql
```
 has still all the databases (I cannot loose them !) 
I have recent backups of all of my sites via Akeeba Backup (site and database included)

Thanks for reading and for your help
Stéphane

---

### Post by MAFoElffen on 2021-08-26
I'm just curious if the database are running or not physically? Or just communications to them are down?

---

### Post by synsteph38 on 2021-08-27
> **MAFoElffen said:**
> I'm just curious if the database are running or not physically? Or just communications to them are down?

Hello MAFoElffen,

I do not know... how could I verify this ?

Thanks for your help and advises

---

### Post by synsteph38 on 2021-08-27
I know where the problem come's from !

I've installed a Joomla! extention that requested some modifications in the Mysql configuration
So I've modified the /etc/mysql/mysql.conf.d/mysqld.cnf file with the following inputs :
```
interactive_timeout = 120
wait_timeout  = 120
connect_timeout = 120
```
and this without stopping MySQL !

I messed all up this way...
But now, how could I rebuild/rewind ?

Thanks for your help and advises
Stéphane

---

### Post by synsteph38 on 2021-08-27
I've uploaded the mysql error log file from yesterday onto my Gdrive, here's the link :
[https://drive.google.com/file/d/1ooBCACZ9NM3GT44tS2o55kM83ePYMDwf/view?usp=sharing](https://drive.google.com/file/d/1ooBCACZ9NM3GT44tS2o55kM83ePYMDwf/view?usp=sharing)

---

### Post by synsteph38 on 2021-08-27
Problem solved !

the error camed form a Joomla! extension. This extension suggested to modify some PHP.ini parameters. Their suggestion is not good !
Set the parameters back to what they should be, and all my sites where back !

---

