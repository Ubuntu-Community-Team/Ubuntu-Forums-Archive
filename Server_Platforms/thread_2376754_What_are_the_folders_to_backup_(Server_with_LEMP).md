---
title: "What are the folders to backup? (Server with LEMP)"
date: 2017-11-05
forum: Server Platforms
---

### Post by xuegdxw on 2017-11-05
Hello, I am fairly new to Ubuntu Server  16.04 and everything.(I have been using Ubuntu for a while, but server is pretty different). I just got my LEMP set up and planning to install WordPress soon. Since server has no GUI, I got Webmin installed just for friendlier remote access. So in the webmin functions, I know I am able to backup folders and etc. The question would be, which folder should I backup? Obviously, I am looking for the core settings, mysql, LEMP and all these... (I have no idea where LEMP is located)
Thanks

---

### Post by deadflowr on 2017-11-05
*Thread moved to **Server Platforms***
Welcome to the Forums.
I've moved your thread to the server sub-forum as the more experienced server users will frequent this place more than *New to Ubuntu*.

---

### Post by SeijiSensei on 2017-11-05
At a minimum you should back up

/etc
/home
/var/lib
/var/log
/var/www

These are the directories that routinely change.  /etc stores all the configuration files.  It can be pretty static after the system is running the way you like it.  On the other hand, it's not very large so I back it up routinely.

/home contains users' home directories.  You may not have much in here given your purposes.

The /var subtree contains files that *var*y like logs or the contents of databases.  MySQL is stored in /var/lib/mysql.  Websites are conventionally placed under /var/www.  The default public web folder is /var/www/html.

If you run other services like mail or DNS, you will have other directories that need backing up.

---

### Post by xuegdxw on 2017-11-06
Thanks for the help guys!

---

### Post by TheFu on 2017-11-07
The File System Hierarchy standards should be helpful to you. Backups aren't just for directories.  You probably need to export/dump any RDBMS objects too, otherwise having the DB files should leave you with corruption.  This can be handled 3 ways - 
a) using an LVM snapshot to prevent any changes to the DB during backups or 
b) by dumping the data or 
c) by shutting down the DBMS during backup periods and grabbing the directories/files.

[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Also, it would be highly useful to have a list of manually installed packages for the system.  apt-mark and dpkg have methods for generating that list and for reloading the list during recovery.

Lastly, if you manually install any tools/programs, then you'd want those as well.  It is common to place those into /usr/local/ ... so I always backup that structure too.

I'm not a fan of webmin.  Best to ensure it only works through an ssh tunnel and is only available through the localhost IP, never from any public IP. Otherwise, it is a security liability.

---

