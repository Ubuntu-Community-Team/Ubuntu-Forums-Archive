---
title: "dealing with mysql users"
date: 2008-12-10
forum: Server Platforms
---

### Post by ShaolinF on 2008-12-10
I am messing around with mysql 5.1.30 on my ubuntu 8.10 setup. I want to host 5 websites on my server, how would I create the accounts for each user? Would I use the adduser method ? And would this automatically set up the user's mysql account too? Or do I have to do that manually (using mysqladmin or something)?

---

### Post by moberry on 2008-12-10
You need to add seperate users for SQL, there are ways to integrate SQL users with directory or local users. But, the default behavior is only local sql users.

---

### Post by ShaolinF on 2008-12-10
Well I am alittle confused at the moment tbh. Say for instance I add a user called johnsmith into group mysql:

useradd johnsmith --gid=1002

Now if I type the following it will log me into johnsmith's mysql area:

mysql -u johnsmith
mysql>

Is this sufficient when setting up a live server ? The thing that worries me is that johnsmith can logon to the mysql server without a password. How do I set a password for him ?

---

### Post by moberry on 2008-12-10
Honestly, I don't know. I have always used sql users within the server itself for connecting with applications.

---

### Post by ShaolinF on 2008-12-10
Thats not a problem - What I am talking about is when you want to host say 20 different websites on one server, each user needs his one account on the server and mysql account too right. Within that mysql account they can create databases/users etc - It looks like when I add a user using useradd, it also creates a mysql account for that user.. Can anyone confirm this?

---

### Post by ShaolinF on 2008-12-10
Thats not a problem - What I am talking about is when you want to host say 20 different websites on one server, each user needs his one account on the server and mysql account too right. Within that mysql account they can create databases/users etc - It looks like when I add a user using useradd, it also creates a mysql account for that user.. Can anyone confirm this?

---

### Post by Philio on 2008-12-10
MySQL has a completely separate user system. To add a user to the system you need to either execute a GRANT statement or it would probably be easier to use phpMyAdmin which will allow you to add users.

---

### Post by ShaolinF on 2008-12-10
Ok thanks for clearing that up. I have a question:
Why do the system users have mysql accounts then? :S

---

### Post by cariboo on 2008-12-10
Nobody except for the user you setup when you installed mysql-server can administer mysql. You have to specifically add users to mysql. If your user doesn't need to administer a database don't set the user up.

Jim

---

