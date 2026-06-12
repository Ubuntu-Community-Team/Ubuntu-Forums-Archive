---
title: "Can't get mysql functions with php"
date: 2005-07-10
forum: Server Platforms
---

### Post by detour on 2005-07-10
Ok it seems that a lot of other people have had problems with php and mysql but none of the solutions I came across have worked for me.

What I've tried:
- installed php4-mysql and apache-mod-auth-mysql packages
- uncommented the mysql.so line in php.ini
- set up root account and created other accounts for mysql
- installed mysql 4.1 since i read about some issue with passwords not authenticating properly or some such

running a phpinfo() page from localhost doesn't display anything regarding mysql, but php -m on the command line does. Trying to use phpmyadmin gives me an error saying that I do not have mysql functions enabled. Am I missing something?

---

### Post by nverhaar on 2005-07-11
Try restarting apache?

I know it may seem like a silly answer, but maybe its been overlooked?

---

### Post by LordHunter317 on 2005-07-11
Sounds like you edited the wrong php.ini to me.  You have to edit the one for the Apache server you're using.

---

### Post by detour on 2005-07-11
Thank you for the replies:

I did restart apache using the following command:
sudo /etc/init.d/apache2 restart (or something like it)

The php.ini that i edited is located in:
/etc/php4/apache2/php.ini

---

### Post by detour on 2005-07-11
So after a bit of messing around I decided to completely remove apache, php, and mysql and begin from scratch using the instructions in the wiki. Apparantly a bad idea... php4-dev fails from a broken dependency, automake, with a failed md5 checksum. I ignored it, and installed eveything else. Things seemed ok, however now when I try to view my phpinfo page, Firefox attempts to download the file. I edited /etc/apache2/apache2.conf and uncommented the lines for the php file handlers and restarted apache, but its the same result.

---

### Post by LordHunter317 on 2005-07-12
Removing stuff because something is broken is almost never a good idea.

Anyway, it doesn't sound like Apache has PHP support loaded, did you reinstall libapache2-mod-php4?

php4-dev isn't what you need to build PHP applications; that is to build modules that are part of the PHP interpreter.

---

### Post by detour on 2005-07-12
I discovered that apache needed to have a LoadModule statement added to the conf file to tell it to load the php module. Everything is working well now, thank you for your help.

---

