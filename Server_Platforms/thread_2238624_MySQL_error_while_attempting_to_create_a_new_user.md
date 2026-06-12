---
title: "MySQL error while attempting to create a new user"
date: 2014-08-09
forum: Server Platforms
---

### Post by Melnik_Hoogland on 2014-08-09
Hi, I have a problem with the tutorial at [https://www.digitalocean.com/community/tutorials/how-to-install-phpbb-forums-on-ubuntu-12-10](https://www.digitalocean.com/community/tutorials/how-to-install-phpbb-forums-on-ubuntu-12-10).

I am up to the point when I am supposed to enter "mysql -Bse "create  user 'phpBB'@'localhost' identified by 'PassWord';"" (don't think this  is relevant, but due to something in my password, I had to use "\ "  instead of double quotes and didn't put single quotes around my  password, and I had to put "-u root -p" before the "-Bse"), but I kept  getting this error:
```
ERROR 1064 (42000) at line 1: You have an error in your SQL  syntax; check the manual that corresponds to your MySQL server version  for the right syntax to use near '(mypassword)' at line 1
```
(real password replaced with "(mypassword)")
After some searching, I found out that this is sometimes caused by the  ";" delimiter. So I tried using "--delimiter=//", before and after the  "-Bse", with and without backslashes before the slashes, and replacing  the ";" with the same thing, but it still gave that error. Finally, I  tried using just "mysql -u root -p" and then, at the MySQL prompt,  entering:
```
DELIMITER //
create user phpBB@localhost identified by (mypassword)//
```
...but it still gave that error. I tried searching the internet, but didn't find any solution.
"mysql --version" outputs "mysql  Ver 14.14 Distrib 5.5.38, for debian-linux-gnu (i686) using readline 6.3".

Thanks in advance.

---

### Post by volkswagner on 2014-08-10
I often find how-to's are inaccurate for current version of MySql.

Here's what has worked for me in the past.  I use two commands.

```
CREATE USER username;
GRANT ALL ON databaseName.* TO 'username'@'localhost' IDENTIFIED BY 'secret';
```

You can change the grant command to make it more restrictive.

---

### Post by Melnik_Hoogland on 2014-08-11
I tried that, but now, in response to the "GRANT ALL ON..." command, it says:
```
ERROR 1046 (3D000) at line 1: No database selected
```

---

### Post by volkswagner on 2014-08-11
Did you enter a valid database name?  You'll need to substitute the database name where I wrote "databaseName.*".

To verify the database name:
```
use mysql;
show databases;
```

You can create an empty database like:
```
CREATE DATABASE NewDatabaseName CHARACTER SET utf8;
```

Replace "NewDatabaseName" with the name of your new database.

---

### Post by Melnik_Hoogland on 2014-08-11
Yes, I have replaced "databaseName.*" with a valid database name, confirmed that it appears in the list of databases, and tried it with and without the ".*" after the database name. It still gives that error.

---

### Post by volkswagner on 2014-08-11
can you post full command that you used?

---

### Post by Melnik_Hoogland on 2014-08-11
I used:
```
mysql -u root -p -Bse "GRANT ALL ON (mydbname).* TO '(myusername)'@'localhost' IDENTIFIED BY '(mypass)';"
```
(those are not the real names/passes that I typed in)
This is after I created the user. Also, my database name has spaces in it.

---

### Post by volkswagner on 2014-08-12
You are asking for trouble with spaces in database names and/or fields.

I'm not sure what -Bpe does, nor why you wouldn't just log into mysql to run your commands.

I'm not an advanced user. I just login to MySQL then run my commands.

```
mysql -u root -p
mysql> GRANT ALL ON databaseName.* TO 'username'@'localhost' IDENTIFIED BY 'secret';
```

I'm not sure why you'd want spaces in db name, but if it's even possible you'll likely need to encapsulate it in quotes.
You'd likely have to encapsulate it in all written code that will access the DB as well.  Again, I don't think this is good practice.

Try creating a test db without spaces and run the command... I think it will succeed.

---

### Post by Melnik_Hoogland on 2014-08-13
I'll try that, but how do I delete my old database that has spaces in it?

---

### Post by nerdtron on 2014-08-14
Use single quotes
```
mysql> drop database 'database with space';
```
or back ticks (key to below the Esc key)
```
mysql> drop database `database with space`;
```
or brackets
```
mysql> drop database [database with space];
```

---

