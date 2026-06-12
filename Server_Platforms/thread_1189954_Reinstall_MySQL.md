---
title: "Reinstall MySQL?"
date: 2009-06-17
forum: Server Platforms
---

### Post by Mycle on 2009-06-17
I recently installed Ubuntu Server 9.04.
During the LAMP installation part I chose to install pretty much everything, so as to err on the safe side.:-)
When it came to the MySQL installation I supplied user and password information but don't remember or have a record of "Database Name".

Later on attempting to install Joomla, I got a 
"Could not connect to database:Could not connect to MySQL" error, after entering my info in the Database Configuration section.

Can I just reinstall the MySQL component of The Ubuntu installation and enter new user name and password etc.?

I've searched and read about some various remedies but these have been explained on the basis of having XAMPP accessible via localhost.

I'm reluctant to completely reinstall Ubuntu for the 6th time, but I will if I must.
-- 
Regards,
Mycle

---

### Post by Cheesemill on 2009-06-17
MySQL doesn't have any databases set up when you install it, you have to create them yourself (which is why you don't have any database names).  From what I remember the Joomla installation instructions guide you through creating a database.

---

### Post by Mycle on 2009-06-17
> **Cheesemill said:**
> MySQL doesn't have any databases set up when you install it, you have to create them yourself (which is why you don't have any database names).  

Thanks, that would explain it. I'd reached the point in the installation of Joomla where the process was asking me for the database name and other user and password info though, which is what I got stuck on.

> **Cheesemill said:**
> 
From what I remember the Joomla installation instructions guide you through creating a database.

I was following those very installation instructions at the time I ran into trouble. I had, wimpishly perhaps,decided to follow the "easy" Browser installation route. "Easy" often has fatal consequences in my experience. But it would be premature to reach such a negative conclusion at this stage. So, I'll run through it all again with my other glasses on.
-- 
Regards,
Mycle

---

### Post by Cheesemill on 2009-06-17
I've just had a look at the Joomla installation instructions for you and realised that it doesn't tell you how to create a database so I'll take you through it.

To create a database with MySQL just do the following:
```
mysql -u root -p
```Then type in the MySQL root password that you chose when installing it, this will get you to a MySQL prompt. We then need to create the database:
```
mysql> CREATE DATABASE joomladb;
mysql> GRANT ALL ON joomladb TO 'joomlauser'@'localhost' IDENTIFIED BY 'joomlapass' WITH GRANT OPTION;
mysql> FLUSH PRIVILEGES;
mysql> QUIT;
```This will create a databse called joomladb with a user joomlauser and a password joomlapass. Substitute these for whatever you wish in the above MySQL code and use them in the web browser installation wizard.

This assumes you are running MySQL on the same machine as your web server.

---

### Post by v3xtra on 2009-06-17
> **Cheesemill said:**
> I've just had a look at the Joomla installation instructions for you and realised that it doesn't tell you how to create a database so I'll take you through it.

To create a database with MySQL just do the following:
```
mysql -u root -p
```Then type in the MySQL root password that you chose when installing it, this will get you to a MySQL prompt. We then need to create the database:
```
mysql> CREATE DATABASE joomladb;
mysql> GRANT ALL ON joomladb TO 'joomlauser'@'localhost' IDENTIFIED BY 'joomlapass' WITH GRANT OPTION;
mysql> FLUSH PRIVILEGES;
mysql> QUIT;
```This will create a databse called joomladb with a user 'joomlauser' and a password 'joomlapass'. Substitute these for whatever you wish in the above MySQL code and use them in the web browser installation wizard.

This assumes you are running MySQL on the same machine as your web server.

Won't you need to create the user first?  Or does that statement understand that there is no user and it creates one?

---

### Post by Cheesemill on 2009-06-17
No need to create the user first, the above commands will do it for you.

---

### Post by Mycle on 2009-06-18
Thanks a lot for the help Cheesemill!

I entered the commands you suggested and all went well until the 3rd line, after which I got:

"Error 1046 (3D000): No database selected"

I did a search on the error and came up with the command:

mysql> use joomladb

I added this after line 2 and the process smoothly completed.

mysql -u root -p

mysql> CREATE DATABASE joomladb;

**mysql> use joomladb**

mysql> GRANT ALL ON joomladb TO 'joomlauser'@'localhost' IDENTIFIED BY 'joomlapass' WITH GRANT OPTION;
mysql> FLUSH PRIVILEGES;
mysql> QUIT;

The new MySQL entries worked beautifully when I went back to the Joomla installation.

I'm so pleased that I was able to avoid the "Good old standby: Reinstallation" 

Thanks one again Cheesemill.
-- 
Regards,
Mycle

---

