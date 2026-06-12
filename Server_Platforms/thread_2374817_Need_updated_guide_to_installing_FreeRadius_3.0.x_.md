---
title: "Need updated guide to installing FreeRadius 3.0.x plus daloRadius on 17.04"
date: 2017-10-19
forum: Server Platforms
---

### Post by daggernc on 2017-10-19
All - after 4 hours of dead-ends and frustration yesterday and countless Google searches and forum searches and even reinstalling Ubuntu 17.04 images, I'm reaching out to the community for some help.  I am pretty much a noob for Linux servers, so I apologize up front if I missed anything simple..

I followed the guide on ubuntugeek.com because it is the newest I can find and used Ubuntu 17.04 and was posted August 4th 2017.  However, it appears that the latest FreeRadius package that now installs has changed things. Everything installs on my Dell server platform (single quad-core Xeon CPU with 16GB of RAM) with no issues. Things start to fail when I get to the point of trying to insert the freeradius database scheme, and the guide for 17.04 says the file location is /etc/freeradius/sql/mysql/schema.sql which produces a no directory/file error.  After digging around on my server, it appears that the schema.sql is in a different location:  /etc/freeradius/3.0/mods-config/sql/main/mysql/schema.sql   So I use that location in the "sudo mysql -root -p radius < /etc/freeradius/3.0/...."  but now I get a "Permission denied" error??  Since I'm new at this I don't want to start messing around and doing chmod's and the like on my own.

Can anybody show me the delta's to the existing guide (freeradius + daloradius) using the latest packages?  

Thanks much in advance,
daggernc

---

### Post by darkod on 2017-10-19
One question before you go too far in the setup. Is using 16.04 an option? You should really use only LTS releases for servers, not necessarily the latest ubuntu version. 16.04 has 5 years support and 17.04 only 9 months.
On another point, I don't think you need to use sudo for mysql data inserting. And make difference between ubuntu root user and mysql root user. I think the command should be something like 'mysql -u root -p radius...' Check out the exacr syntax, don't depend only on that manual. There are many tutorials how to insert data into mysql.

---

### Post by daggernc on 2017-10-19
Thank you darkod for the inputs/guidance.  I actually thought about 16.04 after I d/l and installed 17.04..  I believe what you say about don't need to use sudo for mysql inserting as another guide I found for an earlier install base does a flush then exit and then does the mysql -u root -p ... commands without having to use sudo.  I'll see what other comments I get back and then may try going with 16.04 this evening if no success.  Thanks again.

---

### Post by daggernc on 2017-10-20
Update:  Made good progress and I'd say I'm about 95% there. The key was to use 16.04 (thanks again darkod) and with a few modifications/tweaks I got everything to install and run. I am now stuck at the login to the Web management interface of daloRadius.  I made the changes to daloradius.conf.php and opendb.php to make it work with PHP 7 (and the 'DB Error: Extension not found' error), but now I'm getting a 'DB Error: connect failed' message trying to login to  daloRadius Web page.  Searches on this error message point to a possible user/pswd access rights, but not exactly sure how to proceed from here. I believe I have the right settings in the daloradius.conf.php file. Could it be in sql.conf? or ??  Thanks again.

---

### Post by darkod on 2017-10-20
You need to check in which config file are the credentials that it uses to connect to mysql. They need to be correct (either the mysql root user or another user with required permissions). These credentials might not be in the main config file, they might be in db related .conf file, etc...

But if you have db connect error and the db is on the same server, almost always it is due to bad credentials... Make sure it tries to connect to mysql on correct port too.

PS. Can this help you? [https://sourceforge.net/p/daloradius/discussion/684102/thread/9e633dc4/](https://sourceforge.net/p/daloradius/discussion/684102/thread/9e633dc4/)
Check the second from bottom comment. Basically all say the same, it is credentials issue and make sure it tries to connect to localhost.

---

