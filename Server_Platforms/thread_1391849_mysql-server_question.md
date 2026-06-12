---
title: "mysql-server question"
date: 2010-01-27
forum: Server Platforms
---

### Post by Drenriza on 2010-01-27
Is their somewhere where you can read about (a forum) how to setup & configure a mysql-server database. Information about the driffent folders, where to locate them, commands, and so on.

Thanks on advance

---

### Post by dalitso on 2010-01-27
These might help
[http://www.pantz.org/software/mysql/mysqlcommands.html](http://www.pantz.org/software/mysql/mysqlcommands.html)
[http://www.howtodothings.com/computers/a4590-how-to-learn-mysql-commands.html](http://www.howtodothings.com/computers/a4590-how-to-learn-mysql-commands.html)
[http://forums.mysql.com/](http://forums.mysql.com/)
[http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)

---

### Post by Drenriza on 2010-01-28
When i try to create a database in mysql it just keeps saying that
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'databasename'

???????????

---

### Post by dalitso on 2010-01-28
Are you trying to create the database using webmin?

Sorry, ignore what I said, was replying to a different post and posted it here by mistake.

---

### Post by ICEB3AR on 2010-01-28
looks like the User has no rights to create a database. Try to create one with the root user. If that works then you have to give user the rights to create databases. But this is still a mysql question ;)

By the way. I find it very helpful to use a tool like phpmyadmin or a mysql-client ;) that makes everything easier.

---

### Post by coral66 on 2010-01-28
Try logging in as root ...
mysql -u root

Check privileges ...
select * from mysql.user; 

Give localhost every possible privilege ...
update user set Select_priv	= 'Y', Insert_priv	= 'Y',	Update_priv	 = 'Y', Delete_priv = 'Y', Create_priv	 = 'Y', Drop_priv = 'Y', Reload_priv = 'Y', Shutdown_priv	 = 'Y', Process_priv	 = 'Y', File_priv	 = 'Y', Grant_priv	 = 'Y', References_priv	 = 'Y', Index_priv	 = 'Y', Alter_priv	 = 'Y', Show_db_priv	 = 'Y', Super_priv	 = 'Y', Create_tmp_table_priv	 = 'Y', Lock_tables_priv	 = 'Y', Execute_priv	 = 'Y', Repl_slave_priv	 = 'Y', Repl_client_priv	 = 'Y' 
where Host = 'localhost'; 

That should sort it out.

This is from an old script I saved, so may be out of date with later versions. 
Have you tried a gui for mysql? There are a couple of good ones, I like TOAD, which is free.

---

### Post by Drenriza on 2010-01-28
I have a user with a root password on the server, but how can i change rights for the server so that my user (the only user on the server, can use the datebase) 

If i can find where the database is stored, cant i then on the folders give myself all rights with chmod?

---

### Post by ICEB3AR on 2010-01-28
NO ! as i already said. it is a mysql-query...
You normally do not have to do anything with the files of the server or the files of the database.
Google also helps at those probelms: [http://dev.mysql.com/doc/refman/5.1/en/adding-users.html ]("http://dev.mysql.com/doc/refman/5.1/en/adding-users.html")

OR use as i also said a tool for querying. There you can easily set permissions for the user in mysql !! THOSE PERMISSIONS ARE NOT THE FILEPERMISSIONS OF ANY FILE OF THE SERVER!

---

### Post by John Rivera on 2010-01-28
I would say that after installing Ubuntu server with LAMP option you should install PHPMYADMIN which is easy to use web browser tool for mysql database server management, and it is automated install

---

### Post by Lars Noodén on 2010-01-28
> **Drenriza said:**
> I have a user with a root password on the server, but how can i change rights for the server so that my user (the only user on the server, can use the datebase) 

If i can find where the database is stored, cant i then on the folders give myself all rights with chmod?

The database has its own separate set of users that are not at all in any way part of the operating system.  So the operating system users have nothing to do with the mysql users.  

All activity inside mysql is done using sql and to do that, you connect to the mysql server using the mysql client.  So even [adding mysql users](http://dev.mysql.com/doc/refman/5.1/en/adding-users.html) is done by scripting sql queries.

---

