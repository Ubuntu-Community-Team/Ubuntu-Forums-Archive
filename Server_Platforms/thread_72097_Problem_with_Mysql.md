---
title: "Problem with Mysql"
date: 2005-10-05
forum: Server Platforms
---

### Post by waynejkruse10 on 2005-10-05
I want to create a mysql database so i open up terminal and type:

> sudo mysqladmin -u root -p create phpbb

I enter my root password, then the password i want for the database but i get an error:

> access is denied for user root@localhost (using password: yes)

WTF???? I was using Sudo....

Any help appreciated

Thanks
Wayne

---

### Post by jatos on 2005-10-05
Firstly, if you haven't already got it, install apache/php and then phpmyadmin, itwill make your life a lot easier.

Also try accessing the db without a password, I think instead of using your unix password, mysql by default uses no root passwd

---

### Post by waynejkruse10 on 2005-10-05
i followed the guide on wiki.ubuntu.com to get LAMP working, and the "PHP configuration" error does not bug me any more. I have mysql and Phpmyadmin installed and i can access phpmyadmin with the user root and using no password. However all these databases i can create when i try to link PHPBB up to them i get an error:

I seem to have very little power in MYSQL, i tried doing some of the stuff on this site: [http://dev.mysql.com/doc/mysql/en/adding-users.html](http://dev.mysql.com/doc/mysql/en/adding-users.html) but mysql kept saying access is denied.

---

### Post by diebels on 2005-10-07
1. system login and mysql users are totally unrelated.
2. set a password for mysql user root
Like this:
2.1 get into mysql program
[INDENT]command prompt:>mysql -u root[/INDENT]
2.2 set the password
[INDENT]mysql>SET PASSWORD FOR 'root'@'localhost' = PASSWORD('type in a mysql password for mysql user root here');[/INDENT]

---

