---
title: "MySQL please please please help"
date: 2006-07-31
forum: Server Platforms
---

### Post by uncleclinto on 2006-07-31
Okay, I posted a similar question earlier, but no one responded.  I've installed a beautiful LAMP server on Dapper.  I have a beautiful Moodle just waiting to be moved from my WAMP to the LAMP.  I installed MySQL admin, which I use to make the necessary adjustments to the MySQL database for Moodle.

PROBLEM: I cannot find MySQL admin on the desktop, and as a Linux Noob, I have no idea how to run it from the command line.  "run", for example, apparently is not a command in linux.  Yes, I did RTFM.  Yes I did search all the previous posts on this topic.  Everyone says, "run mySQL admin from the command line".  How?  When "admin@waltersweb:~$" pops up on my little terminal, what do I type to open the MySQL admin program.... or any program for that matter and maybe I can take an educated guess.

Please help!  I only have a week or so left to do this.:-(

---

### Post by Kurt` on 2006-07-31
> **uncleclinto said:**
> Everyone says, "run mySQL admin from the command line".  How?

# mysqladmin

To read how to use it:

# man mysqladmin

---

### Post by uncleclinto on 2006-07-31
Kurt,

Thanks for your quick response!!  :D   I typed "# mysqladmin" at the command line and got another command line.  I then typed "# man mysqladmin" and got another command line.  Nothing opened.  Is it possible my install didn't take or am I missing something??:confused: 

I'm just looking to get this [thing ]("http://www.mysql.com/products/tools/administrator/mysqladmin_users.png") to pop up on my screen.  I know what to do from there.

Thanks

---

### Post by coach-x on 2006-07-31
Make sure you apt-get install mysql-admin
then try mysqladmin at the command line.

---

### Post by uncleclinto on 2006-07-31
as opposed to "sudo aptitude install mysql-admin"?

---

### Post by coach-x on 2006-08-01
Yes, that should work as well.  I just checked my system and it is /usr/bin/mysql-admin or you can just type mysql-admin

---

### Post by uncleclinto on 2006-08-02
okay,  

I opened the folder [usr/bin]("http://www.walterswebdesign.org/screenshot.jpg"), within which I found "mysqladmin".  Clicking or double clicking on it does nothing for me.  Apparently, I need to use the command line, but typing "# mysqladmin" doesn't [open]("http://www.mysql.com/products/tools/administrator/mysqladmin_users.png") anything either.  I tried to move a backed up database to mysql using the command line and that was a complete disaster (see below).  I need the [GUI]("http://www.mysql.com/products/tools/administrator/mysqladmin_users.png") because apparently I'm too darn stupid to move my moodle database without it!  

After taking advice to move my database from Kurt, I “Put it anywhere on the server, then ran the following command: # mysql -p -h DBSERVER dbname < dbname.sql

(Where dbname is the desired database name. and dbname.sql is the path to your backup file. (You'll be promped for the root mysql password).”

Okay, no problem, but when I attempt to run moodle pages on the localhost, I get this message:

"Warning: require_once(C:\waltersweb\moodle/lib/setup.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/moodle/config.php on line 20

Fatal error: require_once() [function.require]: Failed opening required 'C:\waltersweb\moodle/lib/setup.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/moodle/config.php on line 20"

If I could just get to the freaking admin program, I could figure out how to get my database in there.  :confused: ](*,)

---

### Post by uncleclinto on 2006-08-02
ps: I thought downloading "mysql-administrator-1.1.10a-linux-i386.tar.gz.part" might help, but I have no idea where to put it to run the command "shell> tar --directory=/opt -xzvf mysql-administrator-version-linux.tar.gz", which I apparently need to run to install the program.

Why can't I just double click something to install it and double click something to open it?  Why is this such a pain in the tuckus?  Please someone help.  I want to get my moodle on the new server.  My wamp is to darn slow!

---

### Post by uncleclinto on 2006-08-04
Can anybody help me??  Am I just so clueless that no one cares? :(

---

### Post by denni on 2006-08-04
> **uncleclinto said:**
> Can anybody help me??  Am I just so clueless that no one cares? :( try something like this but as always in linux you hawe to hawe some underlying skill to buyld upon ...> apt-get install mysql-server mysql-client libmysqlclient12-dev and make a new mysqladmin account or connect to an existin account with the later command, mysqladmin -u root password yourrootsqlpassword,  
 and then do > man mysqladmin and man mysql

> shell> mysql -h host -u user -p,
Enter password: ********help

> mysqladmin -u root -p localhost
Enter password: ********

---

### Post by hazart on 2006-08-05
Dont run "# mysqladmin" run "mysqladmin", the # before is to tell you that you need to run it as root user.

---

