---
title: "Problem with connecting to MySQL after clean install of 16.04"
date: 2017-01-17
forum: Server Platforms
---

### Post by cscj01 on 2017-01-17
After doing a clean install of 16.04 from a Live DVD.  I backed up my 14.04 installation to a USB drive and am using it to selectively copy files to the 16.04 system.  I have encountered a problem with MySQL though.. I cannot connect to my database because I get the following message:
> ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
This followed the following command```
sudo mysql -u root
```

I was asked for a password that I do not know. Additionally, I must close the terminal session and start over in a new session to try again. If I enter```
sudo mysql -u root
```in the same session, I get the error message with no prompt. Anyone have any insight into this issue?

---

### Post by wildmanne39 on 2017-01-17
*Thread moved to **Server Platforms**.*

---

### Post by cariboo on 2017-01-17
First of all you don't need sudo to use mysql the normal way to access mysql is to use the following command:

```
mysql -u root -p
```

the password is the one you set when you installed mysql. If you aren't sure what the password is, see [here]("https://www.howtoforge.com/setting-changing-resetting-mysql-root-passwords") for instructions on how to reset the password.

---

### Post by cscj01 on 2017-01-17
> **cariboo said:**
> First of all you don't need sudo to use mysql the normal way to access mysql is to use the following command:

```
mysql -u root -p
```

the password is the one you set when you installed mysql. If you aren't sure what the password is, see [here]("https://www.howtoforge.com/setting-changing-resetting-mysql-root-passwords") for instructions on how to reset the password.

I used the instructions at the link for unsure of password:>  Step # 1: Stop the MySQL server process.

Step # 2: Start the MySQL (mysqld) server/daemon process with the --skip-grant-tables option so that it will not prompt for a password.

Step # 3: Connect to the MySQL server as the root user.

Step # 4: Set a new root password.

Step # 5: Exit and restart the MySQL server.

Here are the commands you need to type for each step (log in as the root user):

Step # 1 : Stop the MySQL service:

# /etc/init.d/mysql stop

Output:

Stopping MySQL database server: mysqld.

Step # 2: Start the MySQL server w/o password:

# mysqld_safe --skip-grant-tables &

Output:

[1] 5988ERROR 1054 (42S22): Unknown column 'password' in 'field list'
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[6025]: started

Step # 3: Connect to the MySQL server using the MySQL client:
 # mysql -u root

Output:ERROR 1054 (42S22): Unknown column 'password' in 'field list'

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1 to server version: 4.1.15-Debian_1-logERROR 1054 (42S22): Unknown column 'password' in 'field list'

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>

Step # 4: Set a new MySQL root user password:ERROR 1054 (42S22): Unknown column 'password' in 'field list'

mysql> use mysql;
mysql> update user set password=PASSWORD("NEW-ROOT-PASSWORD") where User='root';
mysql> flush privileges;
mysql> quit

Step # 5: Stop the MySQL server:

# /etc/init.d/mysql stop
ERROR 1054 (42S22): Unknown column 'password' in 'field list'
Output:

Stopping MySQL database server: mysqld
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[6186]: ended

[1]+  Done                    mysqld_safe --skip-grant-tables

Start the MySQL server and test it:At step 4 when entering```
mysql> update user set password=PASSWORD("NEW-ROOT-PASSWORD") where User='root';
```I get the following```
ERROR 1054 (42S22): Unknown column 'password' in 'field list'
```

---

### Post by cariboo on 2017-01-17
> mysql> update user set password=PASSWORD("NEW-ROOT-PASSWORD") where User='root';

PASSWORD should equal your new password eg:

```
mysql> update user set password='aewiL2ee' where user='root';
```

I used pwgen 8 to create a random password.

---

### Post by cscj01 on 2017-01-17
I actually have the password for root now.  I had to keep guessing, and the password for my account worked for root.  I have since been trying to reset my password.  If I do ```
mysql> select * from mysql.users
```, it shows me as a user, but there is nothing where my password should be (the generated hash is missing).  If I try to reset root's password with ```
update user set password='newpassword' where user='root';
``` I get ok for a response. I then flush privileges, but the password is not changed to the new password.  If I try to change my password the same way, I get a message saying there is no matching row in mysql.users.

---

### Post by cscj01 on 2017-01-17
I did a mysqldump of the databases in 14.04 and restored them into the 16.04 release.  I can access these data bases with my root signon, but how do I get my account set up correctly?

---

### Post by darkod on 2017-01-18
Which account are you talking about exactly? You need to be more specific.
And which mysql password are you trying to change, for root user or another mysql user?

---

### Post by cscj01 on 2017-01-18
> **darkod said:**
> Which account are you talking about exactly? You need to be more specific.
And which mysql password are you trying to change, for root user or another mysql user?

First let me say I did a clean install of Ubuntu 16.04 and have a complete backup of my 14.04 system.  I knew I would have to reinstall all the applications that did not come with 16.04.  Many of these had files I could replace after the install and my applications would function corretly without fouling up the install.  With that said, here is what I hope will answer your questions.

I have been talking about two issues, so I'll try to clear it up.  I can sign in as root, but it has the wrong password.  The password root has is the password for the account I had in the previous mysql (5.5) under Ubuntu 14.04.  I want to change root's password to something else.

The second issue is my account I had on mysql 5.5 no longer is recognized by mysql.  I can query mysql.users and see that my account is listed, but if I try to do anything with that account, mysql says there is no row in the table for me.

So in essence, I want to do two things.[LIST=1]
[*]Change root's password
[*]Change my password
[/LIST]
I am running Ubuntu 16.04 x64.  I'm wondering if I need to remove and reinstall mysql.  The fact that root has my account's password under 14.04 (i.e., mysql 5.5) and mysql.users has my account listed, but I can do nothing with it, tells me I must have done something wrong after doing a clean install of 16.04 and re-installs of all the applications.  Maybe I copied a file I should not have over a new file somewhere.  There have been so many applications I have had to install that I could have well made a mistake somewhere.  So far, this is the only problem I've run into.

I hope this makes my situation clearer.

---

### Post by darkod on 2017-01-18
Did you restore only mysql user databases or some system databases too? I don't have much experience with mysql but logically thinking I think there might be issues if you restores system databases too.

I would restore only user data and then create the new users you need in mysql.

If mysql allows you to login with root (which means you know the password), I don't see why it would not allow you to change it. But please make difference between using your linux user password for sudo commands for example, and mysql root user/password. Of course that is not the same.

---

### Post by cscj01 on 2017-01-18
> **darkod said:**
> Did you restore only mysql user databases or some system databases too? I don't have much experience with mysql but logically thinking I think there might be issues if you restores system databases too.

I would restore only user data and then create the new users you need in mysql.

If mysql allows you to login with root (which means you know the password), I don't see why it would not allow you to change it. But please make difference between using your linux user password for sudo commands for example, and mysql root user/password. Of course that is not the same.

Yes, I understand that the system root is different from mysql root.  It's just that things are so strange.  I think I'll see what I can find on the mysql forums.

---

### Post by cscj01 on 2017-01-19
I'll close this issue.  I removed mysql and mysql-workbench and autoremoved the dependicies.  Then I reinstalled.  Things are back to normal.  I suppose I did copy something over.  Lesson learned.  Don't try to get all your environment back to what it was after a clean install in the wee hours of the morning.

---

