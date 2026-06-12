---
title: "Location of MySQL databases"
date: 2009-01-18
forum: Server Platforms
---

### Post by spinstartshere on 2009-01-18
Where are the default MySQL databases stored on the system?  I want to delete them as I think they may be causing problems with other programs.

---

### Post by Masuran on 2009-01-18
Hello, 

You can find the files where MySQL stores its databases in the directory /var/lib/mysql . 
I don't recommend just deleting them however, either remove the databases via MySQL or try to find a real solution to your problem. 

Kind regards,

---

### Post by spinstartshere on 2009-01-18
There's a log in that directory, and it says:

090116 21:21:29 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
/usr/sbin/mysqld: Table 'mysql.plugin' doesn't exist
090116 21:21:29 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
090116 21:21:29  InnoDB: Started; log sequence number 0 46409
090116 21:21:29 [ERROR] /usr/sbin/mysqld: unknown option '--skip-bdb'
090116 21:21:29 [ERROR] Aborting

Any idea if this could be the cause of my problem?

---

### Post by ibutho on 2009-01-18
What happens when you run "mysql_upgrade" as suggested in the output you posted?

---

### Post by spinstartshere on 2009-01-18
Looking for 'mysql' as: mysql
Looking for 'mysqlcheck' as: mysqlcheck
Running 'mysqlcheck'...
mysqlcheck: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) when trying to connect
FATAL ERROR: Upgrade failed

---

### Post by ibutho on 2009-01-18
The 2002 error usually happens if mysql is not running. Try doing
```
/etc/init.d/mysql status
```
If its not running, try
```
/etc/init.d/mysql start
```
After that run the mysql_upgrade.

---

### Post by spinstartshere on 2009-01-18
Trying to start it fails.  No error is given in the terminal.

---

### Post by ibutho on 2009-01-18
Maybe a reinstall of mysql server and related components would solve your problem. Purge mysql (so that you have a clean install) after backing up any important files and then reinstall.

---

### Post by spinstartshere on 2009-01-18
I tried doing that hundreds of times and it wasn't working, but for some reason it's worked this time round.  Thanks for your help.

---

### Post by theDaveTheRave on 2009-01-29
I currently have an MySQL problem, and network connectivity problem!

First.

I have "broken" the mysql databases, and mysql won't start anymore, or rather from the logs it is looking for a specific file, which it can't find, and I don't have a copy of!

So I created the file, with "world read / write" permisions in the location it was saying in the error message (from the error.log).

and still the mysqld daemon can't find the file? I guess it is expecting it to show up in one of the config files, but I can't find reference to how to set / change the location of this file anywhere on the internet.

I was trying to set up a Master/Slave system so as not to have to duplicate all the work that I do in development on my laptop again on my works desktop (I guess I am a bit lazy!), and invariably when I do it the second time I give some of the tables slightly different names (underscores and hyphens) or accidently change the location of a table.

Which is a disaster when I show my boss the various searches that he wants and the data suddenly doesn't work the way I expected it too.

I have been writing scripts to do the work (I am programming them into a new application for my boos and the rest of the team), but as I am experimenting all the time with new stuff I am doing the work in the monitor, saving the "working" commands, then writing the script, then testing it on the desktop etc..... So I figured that I should set up a master slave configuration, which all seems fine but when I reboot the slave, it won't restart. So I have to play with the <my.cnf> file, only this time I have really "screwed" it up and I think I have done something very silly!.... somehow


My other problem is proably easier, and is a potential solution for both problems.

I am contemplating a clean install of my laptop due to a wireless network problem that I can't resolve. However I have my database sitting on the system and all the config files.

I know that I can quite easily use the mysqldump facility, and then save the copy of the <my.cnf> on the laptop etc, but I was wondering if there is an "easier" way where I didn't loose the /var/lib/mysql files?

I have learnt from this though.... Next time around I will create a specific partition for holding the /mysql databases, then I guess once I have done my clean install and put my "saved" my.cnf, back into the /etc/mysql/ folder it will work again as it should?? or am I wrong in this instance??

thanks for the advice, and appologies for the long post... should I have asked this question somewhere else??

David

---

### Post by hyper_ch on 2009-01-29
you can copy the mysql binaries but only do this when mysqld is not running and be sure to md5 the copies.

---

