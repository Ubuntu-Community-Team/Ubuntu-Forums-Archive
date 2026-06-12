---
title: "mysql add user"
date: 2016-08-06
forum: Server Platforms
---

### Post by Vegan on 2016-08-06
i seem to be having some problems manually adding user accounts to MySQL with Ubuntu 16.04

the idea i wanted to to add 2 accounts manually for now to understand the syntax with the changes

CREATE DATABASE databasename;

CREATE USER 'username'@'%' IDENTIFIED BY 'password';

works with this version of Linux, the user in my example is any dweeb with the credential can log in, make sure you use ultra strong passwords

---

### Post by darkod on 2016-08-06
I think you are mixing things up... Are you talking about linux user or mysql user?

For linux user you simply use:
```
sudo adduser <username>
```

For mysql user you first need to log into mysql prompt (usually as mysql root):
```
mysql -u root -p
```

And after that: [http://dev.mysql.com/doc/refman/5.7/en/create-user.html](http://dev.mysql.com/doc/refman/5.7/en/create-user.html)

---

### Post by Vegan on 2016-08-06
I got the databases figured out, user figured out, the users are not local, they are just some user in the cloud

problem now is GRANT is spewing warnings

I have the user, database

GRANT ALL ON database.*

---

