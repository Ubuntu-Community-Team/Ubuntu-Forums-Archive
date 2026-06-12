---
title: "mysql root password - problem following guide"
date: 2007-02-11
forum: Server Platforms
---

### Post by Terry of Astoria on 2007-02-11
I followed the following from the database section of the 6.06 server guide


[INDENT]MYSQL
Configuration

By default, the administrator password is not set. Once you install MySQL, the first thing you must do is to configure the MySQL administrator password. To do this, run the following commands:

sudo mysqladmin -u root password newrootsqlpassword

sudo mysqladmin -u root -h localhost password newrootsqlpassword

[/INDENT]
Here is what I got- an error on the second command. I don't really know what I'm doing. Can someone guide me? As you can see it says connect to localhost failed --?

```
me@pavlov:~/songbook/webmodule$ sudo mysqladmin -u root password someword65	
me@pavlov:~/songbook/webmodule$ sudo mysqladmin -u root -h localhost password someword65
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
```

---

### Post by jtc on 2007-02-11
Those two commands basically does the same thing. If you omit the -h flag it generally connects to the localhost by default. The first command set the new rootpassword, which is fine, since there isn't any. When running the second command there is already a set rootpassword, which mean you can't set a new one, without supplying the old/current one.

[http://dev.mysql.com/doc/refman/5.0/en/mysqladmin.html](http://dev.mysql.com/doc/refman/5.0/en/mysqladmin.html)

---

### Post by Terry of Astoria on 2007-02-11
**Thanks** for enlightening me. I should have thought as much. 
That makes two suggestions I have for the guide-writer(s). However I can't seem to find a way to tell him/her/them. Anyone know how to suggest corrections for the server guide?

---

### Post by gary0 on 2007-02-11
Hi all,
I have followed the instructions given here, but am having serious problems logging in to mysql. It is a fresh install (from fedora core 3), so I followed the instructions and I think I have set a password, but it says Access denied for root@localhost (Using password NO).

Could somebody post verbose instructions on how to do this please? I am new to linux (about 3 days) have set up a fedora server and a dual boot desktop machine - winxp and ubuntu. I am trying to login to mysql on the server itself.

Many thanks,
Gary.

---

### Post by jtc on 2007-02-11
> **gary0 said:**
> ...but it says Access denied for root@localhost (Using password NO).

Let me guess, it doesn't even prompt you for a password? Try adding the -p flag.

```
mysql -u root -p
```

---

### Post by gary0 on 2007-02-11
Yep, that works! Cheers.

---

### Post by william_hunter on 2007-02-24
I am having a similar issue. I can't seem to change the root or user passwords. I follow the commands listed above, but it doesnt seem to stick.\

EDIT: I was able to change the root pw, but  no success in changing the user password. I am also having no luck making a database. This is growing frustrating.

EDIT EDIT: I am stupid. I forgot the ; to close the create database command...Argh!

Anyhow, still having some issues with user passwords, but I can access everything via the root account for now, so I can get started working on the tables I need.

---

### Post by weapon-x on 2007-02-26
hi friends i want to setup my Pc as server so i get this link and so the same as written in [http://www.howtoforge.org/perfect_setup_ubuntu_6.10](http://www.howtoforge.org/perfect_setup_ubuntu_6.10)  there when installingthe mysql i have to run these commands 

mysqladmin -u root password yourrootsqlpassword

mysqladmin -h server1.example.com -u root password yourrootsqlpassword

in this i got an error i skip this step and go on.At the end when i try to install the ISPconfig 
the server name prompted i enter : server1
then user name : root
then password : 123456

there it showes me an error

please help me............:(

---

