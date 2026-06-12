---
title: "Question about root and mySQL"
date: 2010-12-20
forum: Security
---

### Post by ScytheX10 on 2010-12-20
Hi.. I've been getting a little bit more into playing with the practical uses of the programming languages and scripting I've learned ( like many among HTML and PHP/CSS). ]

My question is simple, is it safe to setup a mySQL DB using root? ```
mysql -u root -p
```I'll be primarily using this as a forum board. ( LAMP w/ SMforums)

Edit: My reason for asking is.. I'm used to doing everything as root. I understand this is a bad practice but I've been doing it before Ubuntu.. Really should get out of the habbit and learn to type sudo.

---

### Post by cariboo on 2010-12-20
The mysql root user is different from the system root user, so you're safe using it.

---

### Post by DaithiF on 2010-12-20
for creating your new database you don't have much alternative -- the mysql root user is the only one with permissions to create a new database by default.

its good practice to set up additional mysql users whose rights are limited to a particular database, so that application code accessing the database need not use the mysql root users credentials.

so if you create a database called myforum for example you might want to create a user specific to that database:
```
create user myforum_user@'%' identified by 'somepassword';
grant all on myforum.* to myforum_user@'%';
flush privileges;

```
and then in your application / php / whatever code, use myforum_user when accessing the db.

---

### Post by ScytheX10 on 2010-12-20
> **cariboo907 said:**
> The mysql root user is different from the system root user, so you're safe using it.

Ah, didn't know this.
Thanks!

---

