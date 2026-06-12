---
title: "setting root password in mysql"
date: 2011-08-19
forum: Server Platforms
---

### Post by motomixon on 2011-08-19
Using 11.04, and just installed mysql 5.1.54 using synaptic

I was following the instructions [here]("http://blog.sudobits.com/2011/04/23/how-to-install-mysql-on-ubuntu-11-04/") and the installation when fine,

except that I never got a screen to set the root password.

When I try to set the password using these [instructions]("http://ranjith.zfs.in/mysql-change-root-password/"), following either

 "If you have never set a root password for MySQL" 
$ mysqladmin -u root password NEWPASSWORD


OR, since the first method failed me, then: "However, if you want to change (or update) a root password, then you need to use following command"
$ mysqladmin -u root -p'oldpassword' password newpass

Either way, it fails.
Question:
1) why am I not being prompted to set a root password during installation?
2) what can I do now to fix this??

I am trying to learn Mysql, so please don't presume I know anything about command syntax (cookbook instructions, please!!) For example, the first command above,I tried with with NEWPASSWORD in quotes, and then without. Likewise for the second command.

TIA,Michael

---

### Post by fdrake on 2011-08-19
> **motomixon said:**
> Using 11.04, and just installed mysql 5.1.54 using synaptic

I was following the instructions [here]("http://blog.sudobits.com/2011/04/23/how-to-install-mysql-on-ubuntu-11-04/") and the installation when fine,

except that I never got a screen to set the root password.

When I try to set the password using these [instructions]("http://ranjith.zfs.in/mysql-change-root-password/"), following either

 "If you have never set a root password for MySQL" 
$ mysqladmin -u root password NEWPASSWORD


OR, since the first method failed me, then: "However, if you want to change (or update) a root password, then you need to use following command"
$ mysqladmin -u root -p'oldpassword' password newpass

Either way, it fails.
Question:
1) why am I not being prompted to set a root password during installation?
2) what can I do now to fix this??

I am trying to learn Mysql, so please don't presume I know anything about command syntax (cookbook instructions, please!!) For example, the first command above,I tried with with NEWPASSWORD in quotes, and then without. Likewise for the second command.

TIA,Michael

mysql it's a database system with its own user. the root user of mysql is different from the root user of ubuntu.
try if this work

```

sudo apt-get purge mysql*
sudo apt-get install  mysql-server libapache2-mod-auth-mysql php5-mysql libapache2-mod-php5 openssh-server php5-common php5-cgi

```
it will reinstall mysql and some useful package to be used with it

---

### Post by motomixon on 2011-08-19
Hey, I solved it (or something)

I used sudo dpkg-reconfigure mysql-server-5.1 from the terminal, and was able to set my root password. Now I can log into MySQL Administrator. Presumably things will now work well enough for me to learn how to work this program!!:D

I still don't know why I wasn't given the chance to set the password during installation.  :confused:

---

### Post by fdrake on 2011-08-19
> **motomixon said:**
> Hey, I solved it (or something)

I used sudo dpkg-reconfigure mysql-server-5.1 from the terminal, and was able to set my root password. Now I can log into MySQL Administrator. Presumably things will now work well enough for me to learn how to work this program!!:D

I still don't know why I wasn't given the chance to set the password during installation.  :confused:

?? i don't know why??  at least know you can login-in:p. dont forget to marke the thread as solved.

---

### Post by motomixon on 2011-08-19
> **fdrake said:**
> mysql it's a database system with its own user. the root user of mysql is different from the root user of ubuntu.
try if this work

```

sudo apt-get purge mysql*
sudo apt-get install  mysql-server libapache2-mod-auth-mysql php5-mysql libapache2-mod-php5 openssh-server php5-common php5-cgi

```
it will reinstall mysql and some useful package to be used with it

Hey, thanks for the feedback.
I understand that pw in mysql is different from root user of ubuntu -- the issue was that the installation process was not giving me a chance to set the pw, not even later from the command line, because I couldn't login to mysql to set the pw. However I have solved that (by luck).
I'm going to wait to learn mysql some before proceeding to apache & php. My first attempt to install mysql, using LAMP, was also a fiasco because of the same problem above. Specifically, I couldn't install phymyadmin 'cuz didn't I couldn't enter the (non-existent) pw.
Maybe in a few months I'll figure what the real problem was.

---

### Post by Wim Sturkenboom on 2011-08-19
The procedure would be to restart the mysql daemon with either the *_--skip-grant-tables_* option or (new to me) the *_--init-file_* option.

Info:
[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html)

---

### Post by motomixon on 2011-08-19
> **Wim Sturkenboom said:**
> The procedure would be to restart the mysql daemon with either the *_--skip-grant-tables_* option or (new to me) the *_--init-file_* option.

Info:
[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html)

Another good tip, which I will save.

However, as I just installed Mysql, there was only one account, and that was root (without a password, it would seemed, unless the misbehaving installation also somehow inserted a password unknown to me).  However, I could not login to Mysql as the root, At any rate, I could not have completed the step 1 on the page your link pointed to.

However, I was able to find a solution, which worked fine, given that it was used immediately after installation, and I had no user accounts, and no user data tables.

Thanks for your help
mdm:)

---

### Post by motomixon on 2011-08-19
> **fdrake said:**
>  dont forget to marke the thread as solved.

Oops, I am new to the forum, and didn't notice that option.

Done!!  :)

---

### Post by Wim Sturkenboom on 2011-08-19
I did install mysql on my desktop system (10.04) and it did prompt me. Maybe your install failed for some reason or it's something new in 11.04.

I think that you should have had a *debian-sys-maint* user as well that can be used during updates.

---

### Post by motomixon on 2011-08-28
> **Wim Sturkenboom said:**
> I did install mysql on my desktop system (10.04) and it did prompt me. Maybe your install failed for some reason or it's something new in 11.04.

I think that you should have had a *debian-sys-maint* user as well that can be used during updates.

Hmmm, ok, another maybe VERY useful tip.
What permissions should d-s-m user have?
And are you talking about this user being a Ubuntu account as well as Mysql??

TIA, moto

---

### Post by Wim Sturkenboom on 2011-08-28
It's only a mysql user.

```

mysql> use mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> select user,host,password from user;
+------------------+------------------+-------------------------------------------+
| user             | host             | password                                  |
+------------------+------------------+-------------------------------------------+
| root             | localhost        | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| root             | ubuntu-desktop01 | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| root             | 127.0.0.1        | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| debian-sys-maint | localhost        | *2CEE963D42CF5B97AAB6C932B218194DFF95B0D9 |
| backupuser       | localhost        |                                           |
+------------------+------------------+-------------------------------------------+
5 rows in set (0.00 sec)

mysql> show grants for 'debian-sys-maint'@'localhost';
+----------------------------------------------------------------------------------------------------------------------------------------------------+
| Grants for debian-sys-maint@localhost                                                                                                              |
+----------------------------------------------------------------------------------------------------------------------------------------------------+
| GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY PASSWORD '*2CEE963D42CF5B97AAB6C932B218194DFF95B0D9' WITH GRANT OPTION |
+----------------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)

mysql> exit

```
You can literally copy the 'grant line' above, paste it in the mysql client and press <enter>. Don't forget to flush the privileges; I just added it in example above to show how to use it (just in case ;) ).

---

