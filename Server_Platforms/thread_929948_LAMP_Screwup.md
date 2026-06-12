---
title: "LAMP Screwup"
date: 2008-09-25
forum: Server Platforms
---

### Post by Entropy` on 2008-09-25
Ok, so here's the deal. I'm fairly new to Linux and I wanted to set up a localhost server to continue developing web applications like I did on Windows.
So I installed apache2, php5 and MySQL, and all related packages, but I ran into a few problems. I attempted to remove them using apt-get purge <packages> and reinstalled them. I still had the same problems, so I removed them again using the same method and tried Xampp. PHP didn't seem to run with Xampp, so I attempted to delete it as specified on their site (rm -rf /opt). However, I still got redirect to localhost/xampp when visiting [http://localhost](http://localhost). A reboot and some more screwing around seemed to fix it.
I kept on uninstalling and reinstalling the required software, hoping I would finally get it to work, but I kept having the same problems. I then figured 'perhaps apt-get doesn't remove the configuration files and folders', so I went about deleting everything even slightly related to AMP.

So here I am, unable to get anything to work. Apache2, mysql, php etc won't install, heck nothing will for as far as I can tell. I can't even uninstall anything. Here's a snippet of what I get when attempting to uninstall scrot:
------------------
Removing scrot ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Reloading AppArmor profiles : done.
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
 * Starting MySQL database server mysqld                                 [ OK ] 
/etc/init.d/mysql: line 115: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.
------------------
It just hangs there and I have to kill it using ctrl+c.

I feel like such a noob, is there anyway I can erase my mistakes and make a clean start? I'm running Ubuntu 8.04 64 bit.
Perhaps the best solution would be a (little shell script which would launch a) portable apache2, mysql and PHP package. Like I had on Windows, where a simple batch script would launch apache, php and mysql.

If you need anymore details, let me know. I'm fairly unsure what to information to include. Any help would be appreciated.

PS -
The problems I experienced with Apache2/PHP/MySQL:
- Web pages that functioned fine before stopped functioning, despite using PHP5 on both Windows as Linux. I doubt a change in version would prevent, for instance, include() to stop functioning.
- I had written a little script that would allow me to login to, and manage, MySQL databases. Normally, it would prompt me for login info when a connection to the database hadn't been made yet, however, apparently I got connected right away (that means without having to put in a user or a password), because I was immediately taken to the database-selection screen.

I hope this makes any sense, I'm writing this up in a hurry, and English isn't my first language, so I hope this isn't too confusing.

~ Entropy

---

### Post by kamaji792 on 2008-09-25
It always seems a bit defeatist to start from scratch again.  How about backing up the files you want to keep and doing a server re-build.

You could try this guid [8.04 Lts Hardy Heron server](https://help.ubuntu.com/8.04/serverguide/C/index.html).

Probably not what you want to hear but I think it is what I would do in the same situation.

What were the problems you ran into when you first set the system up?

---

### Post by Entropy` on 2008-09-26
Thanks for your reply, but I would like to keep something like that as a last-resort. I finally managed to uninstall mysql, but I am still unable to reinstall:
----
Setting up mysql-client-5.0 (5.0.51a-3ubuntu5.1) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                                                                                                                     [ OK ] 
Reloading AppArmor profiles : done.
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
 * Starting MySQL database server mysqld                                                                                                                                     [ OK ] 
/etc/init.d/mysql: line 115: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.
----
It hangs after this, my only options is to manually kill it by pressing ctrl+c, which yields the following error:
----
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script killed by signal (Interrupt)
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
----

The problems I were experiencing before my uninstall/reinstall fiasco were related to PHP and MySQL not functioning as expected;
basic functions in PHP wouldn't work for no apparent reason and MySQL would automatically be connected, without having to manually make the connection with @mysql_connect(). More info can be read in the first post.

---

### Post by cariboo on 2008-09-26
If you don't want to reinstall, which in this case I would recommend, you have to remove the startup scripts from /etc/rc,dX to do this for example with mysql:

```
sudo update-rc.d -f mysql remove
```

This will remove mysql start up from all the run levels.

Use the same command if you have any other servers that are misbehaving.

Jim

---

### Post by lykwydchykyn on 2008-09-27
Try using aptitude in place of apt-get, sometimes it's better at sorting out these issues.  Try this and see where it leaves you:

aptitude purge mysql*
aptitude update
aptitude clean
aptitude install mysql-server

I can't be sure, but I'm guessing your original problems may have come from case-sensitivity issues.  I have had this problem a lot when porting web sites over from windows to Linux, and since you mention include() not working, I'm guessing the case of the file name and the case used in your include() statements don't match.  Just a guess.

Case sensitivity takes a bit of getting used to on Linux.

---

### Post by Entropy` on 2008-10-01
You're probably right lykwydchykyn, but that still wouldn't explain my problem with MySQL in the PHP application. Though realizing this in advance could've saved me quite a headache :P

None of those tips worked, I'll paste the shell's output.
```
sudo update-rc.d -f mysql remove
```
---
sudo: unable to resolve host eNtroPC
 Removing any system startup links for /etc/init.d/mysql ...
   /etc/rc0.d/K21mysql
   /etc/rc1.d/K21mysql
   /etc/rc2.d/S19mysql
   /etc/rc3.d/S19mysql
   /etc/rc4.d/S19mysql
   /etc/rc5.d/S19mysql
   /etc/rc6.d/K21mysql
---
So far so good, no errors, but no changes either it seems. No matter how many times I run this command, I get the same output and it doesn't seem to change my situation.

```
aptitude purge mysql*
```
---
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
Couldn't find package "mysql*", and more than 40
packages contain "mysql*" in their name.
Couldn't find package "mysql*", and more than 40
packages contain "mysql*" in their name.
The following partially installed packages will be configured:
  mysql-server mysql-server-5.0 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                                                                                                                     [ OK ] 
Reloading AppArmor profiles : done.
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
 * Starting MySQL database server mysqld                                                                                                                                     [ OK ] 
/etc/init.d/mysql: line 115: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.
---
I have to manually kill it using cltr+c, else it'll just hang at this screen.

*aptitude update* and *aptitude clean* run as expected, but obviously won't really help with my problem because *aptitude purge mysql** didn't execute properly. I tried killing all processes related to MySQL manually and then executing the commands, but that doesn't seem to affect anything.

As a last resort, I'm considering just reinstalling, but I would prefer to find a solution without having to start all over again.

Thanks for all your help so far though, I really appreciate it!

---

### Post by lykwydchykyn on 2008-10-01
Ok, my character match didn't match, apparently mysql* is too vague.
So try 
```

aptitude purge mysql-server mysql-server-5.0

```
I'd be interested in seeing if that fails.

---

### Post by Entropy` on 2008-10-01
Oh, yes, that seems to have fixed it! I LOVE YOU lykwydchykyn! You saved me so much time :D I thanked you for your post, you really deserved it.
Also, thanks a lot to anyone else who tried to help me, I really appreciate it! :D

---

### Post by Hypnoz on 2009-05-11
I had this same issue and this is how I solved it. The key is the part of the error that says 
/etc/init.d/mysql: line 115: /etc/mysql/debian-start: No such file or directory

If you check /etc/mysql/ you will notice there is no file named debian-start but this file is necessary. I'm not sure how it gets removed, but you need to recreate it.

In /etc/mysql/ create a new file named debian-start, give it chmod 755 permissions (rwxr-xr-x), and paste this text into it.

#!/bin/bash
#
# This script is executed by "/etc/init.d/mysql" on every (re)start.
#
# Changes to this file will be preserved when updating the Debian package.
#

source /usr/share/mysql/debian-start.inc.sh

MYSQL="/usr/bin/mysql --defaults-file=/etc/mysql/debian.cnf"
MYADMIN="/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf"
MYUPGRADE="/usr/bin/mysql_upgrade --defaults-extra-file=/etc/mysql/debian.cnf"
MYCHECK="/usr/bin/mysqlcheck --defaults-file=/etc/mysql/debian.cnf"
MYCHECK_SUBJECT="WARNING: mysqlcheck has found corrupt tables"
MYCHECK_PARAMS="--all-databases --fast --silent"
MYCHECK_RCPT="root"

# The following commands should be run when the server is up but in background
# where they do not block the server start and in one shell instance so that
# they run sequentially. They are supposed not to echo anything to stdout.
# If you want to disable the check for crashed tables comment
# "check_for_crashed_tables" out.
# (There may be no output to stdout inside the background process!)
echo "Checking for corrupt, not cleanly closed and upgrade needing tables."
(
  upgrade_system_tables_if_necessary;
  check_root_accounts;
  check_for_crashed_tables;
) >&2 &

exit 0

---

