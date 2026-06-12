---
title: "phpbb2-conf-mysql error!"
date: 2007-02-21
forum: Server Platforms
---

### Post by mrpeenut24 on 2007-02-21
I'm trying to install phpbb2 via phpbb2-conf-mysql, but it keeps giving me an error: 
> 
FAILURE: Tables not created
The configuration script failed to create the phpbb tables. Please run
dpkg-reconfigure phpbb2-conf-mysql, to try with different options, or
don't use phpbb2-conf-mysql at all.
Error: Error when trying to connect to the mysql database.   
I've run dpkg-reconfigure multiple times in-between apt-get removing phpbb2 and reinstalling, but it keeps giving me the same error.  Mysql is running and I can view the databases in phpmyadmin.  There was a phpbb2 database, but I removed it when I tried to reinstall it, and now it's not coming back up.  How can I do a complete removal so I can reinstall this?  Or how else can I install this?

I've tried creating the database in mysql manually, and going to 'localhost/phpbb/' but it gives me an error:
> 
phpBB : **Critical Error** 

Could not query config information

**_DEBUG MODE_**

SQL Error : 1146 Table 'phpbb2.phpbb_config' doesn't exist

SELECT *     FROM phpbb_config

Line : 218
File : common.php
Help would be greatly appreciated!

---

