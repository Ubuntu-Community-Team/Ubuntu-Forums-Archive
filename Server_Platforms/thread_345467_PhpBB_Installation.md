---
title: "PhpBB Installation"
date: 2007-01-24
forum: Server Platforms
---

### Post by chipdip on 2007-01-24
I just attempted to install the newest version of PhpBB from [http://www.phpbb.com/](http://www.phpbb.com/), following the install instructions, I installed apache2 and mysql (Newest version in the repos), I placed the PhpBB folder contents into /var/www/, and then went to chipdip.kicks-***.org:8080, which brought me to the PhpBB installation page. The settings I selected were:

```
Default Board Language: English
Database Type: Mysql 4.x/5.x
Installation Method: Install

Database Server Hostname: localhost
Your Database Name: base
Database Username: chipdip
Database Password: ********
Prefix: phpbb_

Admin Email Address: chipdip@verizon.net
Domain Name: chipdip.kicks-***.org
Server Port: 8080
Script Path: /var/www/
Admin Username: chipdip
Admin Password: ********
Admin Password (Confirm): ********
```

When I Select those settings and hit "Start Install", I get an error stating:

```
An error has occurred during installation
The PHP configuration on your server doesn't support the database type that you chose
```

---

### Post by darrenm on 2007-01-24
> **chipdip said:**
> I just attempted to install the newest version of PhpBB from [http://www.phpbb.com/](http://www.phpbb.com/), following the install instructions, I installed apache2 and mysql (Newest version in the repos), I placed the PhpBB folder contents into /var/www/, and then went to chipdip.kicks-***.org:8080, which brought me to the PhpBB installation page. The settings I selected were:

```
Default Board Language: English
Database Type: Mysql 4.x/5.x
Installation Method: Install

Database Server Hostname: localhost
Your Database Name: base
Database Username: chipdip
Database Password: ********
Prefix: phpbb_

Admin Email Address: chipdip@verizon.net
Domain Name: chipdip.kicks-***.org
Server Port: 8080
Script Path: /var/www/
Admin Username: chipdip
Admin Password: ********
Admin Password (Confirm): ********
```

When I Select those settings and hit "Start Install", I get an error stating:

```
An error has occurred during installation
The PHP configuration on your server doesn't support the database type that you chose
```

Have you installed php4-mysql ?

---

### Post by chipdip on 2007-01-24
Yes, php4-mysql is installed.

---

### Post by Nik_Doof on 2007-01-24
Check that theres an entry for mysql module in /etc/php4/apache/php.ini

```
extension=mysql.so
```

If not, add it in then restart apache.

---

### Post by darrenm on 2007-01-24
phpBB2 or 3?

edit: You don't seem to have PHP parsing at all now ;)

---

### Post by chipdip on 2007-01-24
> **Nik_Doof said:**
> Check that theres an entry for mysql module in /etc/php4/apache/php.ini

```
extension=mysql.so
```

If not, add it in then restart apache.

Alright, did that, but as stated before, I dont seem to be able to parse php anymore. :P
Not exactly sure what I did that caused that.

---

### Post by chipdip on 2007-01-24
I think Im going to do it the right way this time. I am going to install the server edition on an unused PC.

---

### Post by darrenm on 2007-01-24
Congrats dude, it seems to be working now ;)

---

### Post by chipdip on 2007-01-24
Umm... It does? I cant seem to get it working through my computer. I am using sureproxy to connect to it, and it still shows that Firefox wants to download the file. I just installed the standard Ubuntu Desktop fresh, and ran "sudo apt-get install php5 mysql-server apache2 libapache2-mod-php5". I cant seem to get it working from where I am.

---

### Post by chipdip on 2007-01-24
Thank you very much, I got it, Installed PhpBB, now I'm all ready to rock! Apparently the proxy itself is what was causing the problem. Thanks! :D

---

