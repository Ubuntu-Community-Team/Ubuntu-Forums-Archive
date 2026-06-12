---
title: "Ubuntu 10.10 LAMP web-server problem"
date: 2011-02-16
forum: Server Platforms
---

### Post by Jefferythewind on 2011-02-16
Hi everyone,
  I just tried the whole installation process twice:

Install ubuntu server 10.10 with the LAMP bundle and openSSH.  After installation I test the web server by opening the IP in a remote web browser, and it is successful.

  I am trying to restore a backup joomla file using akeeba backup, and everything "looks" good, the mysql DB is restored and all the files are there, that I can see.  

  The problems are:
1) that once I restore the joomla backup, I try to hit the joomla main site, and I get the HTML 500 error.  I checked the error log, and I get an insufficient memory overload for one of the php files in joomla.  

2) Also I cannot remotely access the mysql database.  I get the mysql 2003 error.

  So i know these questions aren't exactly ubuntu's problem, but I thought I would see if these errors mean anything to any of you.

---

### Post by Neo@Matrix on 2011-02-16
> **Jefferythewind said:**
> 
1) that once I restore the joomla backup, I try to hit the joomla main site, and I get the HTML 500 error.  I checked the error log, and I get an insufficient memory overload for one of the php files in joomla.  

You should define larger amount memory for processing PHP than the default 8-16Mb. In my case I dedicated 512Mb from 8Gb.
> 
2) Also I cannot remotely access the mysql database.  I get the mysql 2003 error.
.
In MySQL install process there was a question like :Allow remote access?...
Later U can change permission for remote access in MySQL settings too.
Hope it helps.

---

### Post by tgalati4 on 2011-02-16
Try increasing your memory limit in /etc/php5/php.ini.  When you reinstall, you go back to the default settings.  Joomla, drupal and other content management systems need large RAM reserves to process the PHP code.  Your default is probably 8M or 16M and you need 96M or 128M.

---

### Post by Jefferythewind on 2011-02-16
Hi, thanks for the quick responses, actually i should have mentioned that I already tried changing the php.ini file and gave it a much larger limit.  Right now the default is already 128M, which i guess is the maximum.

I have found my problem in the mysql configuration file, and I commented out the "skip-external-locking" line, restarted the machine, but I still can't access it remotely... hmmm

---

### Post by Jefferythewind on 2011-02-16
OK so I sorted the problem on the mysql db, I had "localhost" for the bind-address in the my.cnf file, and when I changed it to the IP of the server, it worked for remote connections, so that is cool, i still can't access the website though, html 500 error.

---

### Post by Neo@Matrix on 2011-02-16
Have U checked the www config start directory?

---

### Post by Jefferythewind on 2011-02-17
sorry i don't know exactly what you mean by www config start directory.  But i know that the directory where the website resides is in the right spot.  I set it up in the /etc/apache2/sites-enabled/000-default file.  And when I put a different test file, like info.php, it works and I can see it.  I think the whole problem may be with mysql, because actually I still cannot connect to mysql remotely...

---

### Post by Jefferythewind on 2011-02-17
sorry, actually I can connect to mysql remotely now.  It was a problem with Grant privileges inside mysql.

---

