---
title: "how to create new database"
date: 2010-03-30
forum: Server Platforms
---

### Post by tonjaa on 2010-03-30
ubuntu 9.10 64 bit
i try to install XAMPP and i want to create new database by use phpMyAdmin 
at MySQL localhost  create new database it show No Privileges 
how to create new database from terminal please guide to me by step .

---

### Post by Ryan Dwyer on 2010-03-30
You need to log into MySQL as a user who has permission to create databases. This is usually root, and the password is blank unless you set one when installing.

---

### Post by tonjaa on 2010-03-30
i think when i login i have one password i don't know why i can't create it.

---

### Post by s_ø on 2010-03-30
The user your are using is not allowed to create databases.
At phpmyadmin login screen use root as the login name.
After login, either create the databases you need, or click the privileges tab and grant your normal user right to create database.

Why are you using XAMPP?
If it is a fresh install, I would suggest you removed the XAMPP package and install LAMP instead.

---

### Post by tonjaa on 2010-03-30
thank you so much i can create database by change name from pma to root 
and create password login phpmyadmin by root .

---

