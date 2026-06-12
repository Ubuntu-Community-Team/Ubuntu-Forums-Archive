---
title: "Mysql server prob ..."
date: 2005-10-28
forum: Server Platforms
---

### Post by dbee on 2005-10-28
root@ubuntu:/var/www/apache2-default/mambo # /etc/init.d/mysql restart
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.
Checking for crashed MySQL tables in the background.

anyone know what this means ???

Also ... the best way to find the userid of my webserver mysql account ?

I know what it is intuitively - but what's the best way to check for sure ?

---

### Post by LordHunter317 on 2005-10-28
It means it's doing what it's supposed to be doing?

And look at /etc/passwd...

---

### Post by dbee on 2005-10-28
Hi LH,

the problem I have at the moment is that I'm installing a new version of mambo just to have a look at it ... 
It's installation page on my server tells me that there is no mysql support ...

I have the mambo configuration file looking something like this...

$mosConfig_host = 'localhost';  // This is normally set to localhost
$mosConfig_user = 'username';       // MySQL username
$mosConfig_password = 'password';   // MySQL password
$mosConfig_db = 'Mambo';        // MySQL database name

I can log into my mysql server and Mambo table from the command line using the above info no problem. 

But it doesn't seem to want to do it from the webserver ... arragghhh !!

mysqld runs as mysql user ... but I'm not sure whether that makes much of a difference ...

---

### Post by LordHunter317 on 2005-10-28
You're missing php4-mysql, likely.

---

### Post by dbee on 2005-10-28
Damn your good LH :) 

My phpinfo() page says that php was configured --without-mysql 

Synaptic says that it's installed .... I reinstalled php4-mysql but there was no effect.

What should do now then ... just reinstall everything ?

---

### Post by dbee on 2005-10-28
Err ... so now I think that I've two versions of php on the system

I've got the one that returns from 

whereis php 

it shows up as php5 from

php -v

but my webserver shows that it's using php4.***

the php5 has SQLite complied in,

---

### Post by dbee on 2005-10-28
Ok then, I had two versions of php installed, it worked when I removed the php5 ...

Thanks anyway

---

