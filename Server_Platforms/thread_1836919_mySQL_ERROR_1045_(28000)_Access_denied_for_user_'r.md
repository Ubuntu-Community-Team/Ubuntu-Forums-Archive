---
title: "mySQL ERROR 1045 (28000): Access denied for user 'root'@'localhost"
date: 2011-08-31
forum: Server Platforms
---

### Post by BlackWhiteAndRed on 2011-08-31
I can't get mySQL to run even though I have the correct password.
 

I was  having problems directing a localhost and I tried fixing things in  myphpadmin.  I deleted my root directory/privileges in phpmyadmin and then things took a turn for  the bad.  mySQL could no longer run and I have no idea how to fix it.

  
 I've tried reinstalling phpmyadmin and everything related to mySQL  and still do not have any luck getting it to run.  I know mySQL is  running because when I type in:
  ps -ef | grep mysql
 I get
mysql     1149     1  0 20:23 ?        00:00:00 /usr/sbin/mysqld
jeremy    2314  2283  0 20:34 pts/0    00:00:00 grep mysql
 When I type in: "mysql -u root -p" and enter the password I get reset I get the message:

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
 I've tried using an init file and loading it from there, resetting  passwords and using dkpg to reset things but still have no luck.


If I type the command:
mysqld  --skip-grant-tables


I get
110831 20:57:24 [Warning] Can't create test file /var/lib/mysql/jeremy-laptop.lower-test
110831 20:57:24 [Warning] Can't create test file /var/lib/mysql/jeremy-laptop.lower-test
110831 20:57:24 [Warning] One can only use the --user switch if running as root



 Does anyone ever had this happen to them or know how to fix it?

---

### Post by Wim Sturkenboom on 2011-09-01
Run your last command using sudo after stopping the mysql service
```

sudo service mysql stop
sudo mysqld --skip-grant-tables

```
The latter wiil, in my experience, not return to a command prompt

In another terminal, start the mysql client and select the mysql database. If the root user entries are still there, just set a password using *_update user set password=password('yourpassword') where user='root'_*.

If there are no root entries, use *_grant all privileges on *.* to 'root'@'localhost' identified by 'yourpassword' with grant option_*.

Next exit the client, find the pid of the running mysql daemon and kill it.

Start the mysql daemon using *_sudo service mysql start_* and try again to get in.

PS you can ignore warnings about lower-test and higher-test.

---

### Post by BlackWhiteAndRed on 2011-09-01
I tried what you suggested and get the following error:

ERROR 1290 (HY000): The MySQL server is running with the --skip-grant-tables option so it cannot execute this statement

I assume the "--skip-grant-table" creates a read-only of the database and when I try to write something it screams at me.  

Any other suggestions?

---

### Post by Wim Sturkenboom on 2011-09-01
Sorry, I should have checked

OK, I hope you have not done more damage by also deleting the debian-sys-maint user in mysql ;)

Have your mysql daemon running the normal way. Start your mysql client as shown below
```

mysql -u debian-sys-maint -p

```
In another terminal, 'cat' the file *_/etc/mysql/debian.cnf_*. That file contains a password; paste that password when prompted for it.

The debian-sys-maint user has full privileges so you should be able to run the earlier mentioned grant statement. Don't forget to flush the privileges before quiting the client.

Good luck.

PS
All honours go to speedman who posted this in [http://ubuntuforums.org/showthread.php?t=27156&page=2](http://ubuntuforums.org/showthread.php?t=27156&page=2) (post #12)

---

### Post by BlackWhiteAndRed on 2011-09-03
Worked! Thanks so much for helping me out and linking me to the right thread.

---

### Post by Wim Sturkenboom on 2011-09-04
Great. Please mark your thread as solved using the thread tools just above the first post on this page.

---

### Post by ian.d.rossi on 2011-10-27
Thank you so much Wim and speedman. I experienced this same problem while installing mysql-server and related packages as well as phpmyadmin. **I think this is a bug.**

I was able to log into mysql through the CLI and phpmyadmin and then I started getting 'root'@'localhost' access denied errors. A full purge/removal of mysql didn't work.

Thankfully, this post did the trick for me and saved the rest of my hair. :)

Ian Rossi

---

### Post by samyakd on 2012-09-26
After I do all this and i type "SET PASSWORD FOR root=PASSWORD('')" i get this: 

ERROR 1290 (HY000): The MySQL server is running with the --skip-grant-tables option so it cannot execute this statement


Please help. Thanks.

> **Wim Sturkenboom said:**
> Sorry, I should have checked

OK, I hope you have not done more damage by also deleting the debian-sys-maint user in mysql ;)

Have your mysql daemon running the normal way. Start your mysql client as shown below
```

mysql -u debian-sys-maint -p

```In another terminal, 'cat' the file *_/etc/mysql/debian.cnf_*. That file contains a password; paste that password when prompted for it.

The debian-sys-maint user has full privileges so you should be able to run the earlier mentioned grant statement. Don't forget to flush the privileges before quiting the client.

Good luck.

PS
All honours go to speedman who posted this in [http://ubuntuforums.org/showthread.php?t=27156&page=2](http://ubuntuforums.org/showthread.php?t=27156&page=2) (post #12)

---

### Post by Wim Sturkenboom on 2012-09-26
> **samyakd said:**
> After I do all this and i type "SET PASSWORD FOR root=PASSWORD('')" i get this: 

ERROR 1290 (HY000): The MySQL server is running with the --skip-grant-tables option so it cannot execute this statement


Please help. Thanks.

Run the mysql daemon the normal way (so not using skip-grant-tables).

Use the debian-sys-maint user as described to login, change to the mysql database and issue the correct command to set the root password.

---

### Post by jpvasconcelos on 2012-11-17
Thx Win... you save us ofc! ;D

I was some days searching for a solution and found it here! very thanks! :D

---

### Post by SripatiDas on 2012-12-12
I was some hours searching for a solution to unlock locked mysql root user and found it here! very thanks! :D[/QUOTE]

---

### Post by RAMDrive on 2013-01-10
Trying to install asterisk on the Reapberry Pi, thanks for solving one of many problems

---

### Post by melc_sokat on 2013-04-21
Works for me also. Thank you.

---

### Post by paulindivica on 2013-07-15
When I try to use the debian-sys-maint user as described above I get:

ERROR 1045 (28000): Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)

Any ideas?

---

### Post by Dedeobi on 2014-04-11
> **paulindivica said:**
> When I try to use the debian-sys-maint user as described above I get:

ERROR 1045 (28000): Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)

Any ideas?

I have some problem, I was remove all user except root user in MySQL. 

Can you tell me how to fix it?

---

### Post by Ubi_one_2014 on 2014-04-12
what happaneds when you access mysql by using phpmyadmin?

---

