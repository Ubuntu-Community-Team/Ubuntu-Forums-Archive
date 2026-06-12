---
title: "wrong chmod broke LAMP server integrity 12.04LTS"
date: 2013-04-21
forum: Server Platforms
---

### Post by stivalet on 2013-04-21
Hello Ubuntu comunity

I'm not an expert in linux but few month ago I decided to star my first ubuntu server for development on web based applications and web design.

The problem: I broke the databases and sudo stop working after mistype a wrong chmod command. I was trying to modify file permisions on sub folder under /var/www/subforder using sudo chmod -R 775 *

Instead that I added by mistake a /

sudo chmod -R 775 /*

And it started doing changes from the root directory, I saw a bunch of errors and I realized that I mess it up and cancelled that using ctrl^c

after that my databases were broken as follows :(:

pulsecomputer.net (only as a reference link to my server, where the error is shown)

 Database error > Error establishing a database connection

on other site it shows the login page but after input the user and password gives me:

SQLSTATE[HY000] [2002] Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I have not SSH access anymore: "Network error: software caused connection abort"


and from the computer where the system is installed SUDO stoped working and show the next error when I try to use it:

 sudo: /usr/lib/sudo/sudoers.so must be only writable by owner
sudo: fatal error, unable to load plugins

MySQL root login also does not grant me access:

:~$mysql -u root -p
 ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Man I'm very upset about my stupidity, I have a lot of work invested on these projects.

Any help is highly appreciate, many thanks in advance.

---

### Post by stivalet on 2013-04-22
Update: certain folders into /var became read only 

/var/lib /var/run are in read only mode, I restarted and logged as root using recovery mode from grub and tried to chmod them to -rwxr-xr-x but nothing happened: "operation denied read only file system"

If i go to /var/www I'm able to edit files and folders

any idea to change that back to normal?

---

### Post by capscrew on 2013-04-22
The quickest way to resolve your problem is to backup the data and reinstall the OS.  I know this sounds trite and simplistic.  The errors cover a wide range of permissions and you will never find them all.  This could affect the system for a long time.  The install should take less than a few hours at most.  Hopefully you have notes of your configuration of the LAMP server.

---

### Post by stivalet on 2013-04-22
Thanks you capscrew I concur on that. The only and biggest problem is to pull out the MySQL databases. Is there any way I export them under these conditions?

---

### Post by capscrew on 2013-04-22
> **stivalet said:**
> Thanks you capscrew I concur on that. The only and biggest problem is to pull out the MySQL databases. Is there any way I export them under these conditions?

You just have to try it.  I have no MySQL experience.

---

### Post by JohnFeist on 2013-04-24
The data files are kept in /var/lib/mysql  if you export them, including folders you should be able to reestablish them after you do the reinstall.

---

### Post by SeijiSensei on 2013-04-25
If the MySQL server is still running, use mysqldump to create a backup of the database in plain text.  Read it back with the mysql command-line client after the machine is rebuilt.  Use the "--all-databases" command-line switch to back up the entire system.

If the MySQL server will not start, then you are left with backing up the contents of /var/lib/mysql as JohnFeist suggests.  The last time I tried this method, installing MySQL onto an existing database, it worked correctly, but I'm always wary of possible conflicts resulting from different server versions.  If you install the identical version of MySQL, this method should work.

---

### Post by stivalet on 2013-04-27
Thank you all guys, I managed to solve this problem.

I did'nt have a chance to try SeijiSensei solution, I tried what JohnFeist sudgested on another computer but I wasn't able to make it work this way, the databases where there but it had permitions issues I mess a lot with the permitions and nothing so i decided to try something else.

My dirty solution: I re-installed  once again ubuntu server 12.04 on top of my filesystem without re-formating it, worked like a charm :P now I had the chance to export my databases and do a clean install.

:cool:

---

### Post by stivalet on 2013-04-27
How do I flag this thread to solved? :P

---

