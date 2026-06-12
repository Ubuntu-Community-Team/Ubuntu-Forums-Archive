---
title: "My mysql suddenly stooped working"
date: 2011-08-03
forum: Server Platforms
---

### Post by Tystick86 on 2011-08-03
I ran $ mysql -u root just like any other day but alas today was not just any other day I received

$ mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I don't remember doing anything out of the usual. I looked it up and people recommended purging mysql and then reinstalling but I spent 4 hours creating a schema for a rails app I am designing and would really appreciate if an Ubuntu guru out there could help me keep my databases.

Thanks everyone hope all is well

---

### Post by rudelgurke on 2011-08-03
Is there something inside /var/lib/mysql/ ? And what does mysqld.err say after trying to start MySQL manually ?

And - to your command - doesn't your "root" account of MySQL has a password ?

---

### Post by Tystick86 on 2011-08-03
$ sudo ls -al /var/lib/mysql
total 28700
drwx------  6 mysql mysql     .
drwxr-xr-x 81 root  root      ..
drwx------  2 mysql mysql     bandmates_development
drwx------  2 mysql mysql     bandMates_development
drwx------  2 mysql mysql     bandmates_test
drwx------  2 mysql mysql     bandMates_test
-rw-r--r--  1 root  root      debian-5.1.flag
-rw-rw----  1 mysql mysql     ibdata1
-rw-rw----  1 mysql mysql     ib_logfile0
-rw-rw----  1 mysql mysql     ib_logfile1
-rw-rw----  1 root  root      mysql_upgrade_info

I couldn't find mysqld.err

I don't have a password set its just for development

Thank you for your help

---

### Post by rudelgurke on 2011-08-03
And where's the "mysql" database to store user accounts etc. ?

Make a backup of this directory, run mysql_install_db and copy in the content of your backup.

Should fix it

---

### Post by /r007 on 2011-08-04
Have you checked the MySQL service is running as that error just means it got no response from the MySQL daemon 

service mysqld status

If its stopped or locked just restart it

service mysqld restart

If its running give it a restart just incase

If you get any errors during service restarts or this hasnt resolved the problem look in /var/log/mysqld.log and /var/log/messages for any errors and post them

---

### Post by rudelgurke on 2011-08-04
Without an existing "mysql" database, the server won't start. So - creating that one and it should work without problems. :)

---

### Post by Tystick86 on 2011-08-15
Thank you for the replies everyone. Sorry it took so long to get back to you all. One of those months of extreme business. I tried restarting the service with /etc/init.d/mysql restart and start both told me I should use a newer command which I tried and got a error but it was a while ago so I don't remember it.

I did sudo apt-get purge mysql-server-core-5.1
then sudo apt-get install mysql

and it works again and even better all of my data was retained.

When the problem occurred I used the mysql admin gui app and usually I just use command line. I don't know if it could have caused the problem but I shut my computer down with sudo init 0 and the gui was still running.

Thank you again everyone

---

