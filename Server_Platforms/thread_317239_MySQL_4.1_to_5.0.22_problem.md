---
title: "MySQL 4.1 to 5.0.22 problem"
date: 2006-12-12
forum: Server Platforms
---

### Post by Gweniviere on 2006-12-12
I recently updated my MySQL from 4.1 to 5.0.22 and now I can't use mysql-administrator or MySQL Workbench to change the passwords of users. 

Is there a script I need to run or something that modifies the mysql tables?

---

### Post by Terryj1974 on 2006-12-12
What error message(s) do you get when you try to update the passwords? I have a couple of ideas that might help, but wanted to get more information to work with.

TJ

---

### Post by Gweniviere on 2006-12-12
**mysql-administrator 1.26 rc**
The users are displayed but all dimmed out and no actions can be performed on them. 
I can add a new user, but when I try to assign privileges I get this error...
Error while storing the user information. The suer might been deleted. Please refresh the user list.

And a DOS prompt comes up and says ** Message: save user: can't retrieve user information. Closing this dos prompt causes mysql-administrator to close.

**mysql-administrator 1.1.5**
Clicking on a user produces this error...
Error while fetching user information. The following error occufed: Unknown column 'Creat_view_priv' in 'field list' (1054)

**mysql client**
And finally, when I try add a user or using...
grant all privileges on test.* to 'gwen'@'%' identified by 'password';
the user is added to the mysql.user table, but all privs are set to N.

---

### Post by Terryj1974 on 2006-12-12
Do you know what ip your MySQL server is bound to? By default in mysql 5 it is bound to localhost.

Go to the /etc/mysql/my.cnf file, and check to see what address it is bound to. If it still says localhost - comment out that line.

Let me know if this helps!

TJ

---

### Post by Gweniviere on 2006-12-12
> **Terryj1974 said:**
> Do you know what ip your MySQL server is bound to? By default in mysql 5 it is bound to localhost.

Go to the /etc/mysql/my.cnf file, and check to see what address it is bound to. If it still says localhost - comment out that line.

Let me know if this helps!

TJ

It's not bound to localhost. In fact, I can access the machine remotely with no problems, either with mysql client or mysql-administrator and perform things like editing tables, creating indexes etc. The only thing that seems to be affected is managing users.

---

### Post by Terryj1974 on 2006-12-12
From what you have described, it sounds like you will need to run the mysql_upgrade command, which is usually the last thing I do when I upgrade.

To run mysql upgrade type in:


***sudo /usr/bin/mysql_upgrade --user=root --password=password***


I also found some documentation from MySQL that details more of what this does. The link is:

[http://dev.mysql.com/doc/refman/5.0/en/mysql-fix-privilege-tables.html](http://dev.mysql.com/doc/refman/5.0/en/mysql-fix-privilege-tables.html)

Please let me know if this helps!!

Terry

---

### Post by Gweniviere on 2006-12-12
:p :p :p That's what I needed! Thanks a bunch!:p :p :p

---

