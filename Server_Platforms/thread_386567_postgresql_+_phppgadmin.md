---
title: "postgresql + phppgadmin"
date: 2007-03-17
forum: Server Platforms
---

### Post by koumi on 2007-03-17
Hi 

I installed on ubuntu 6.06 postgresql 8.1 and the management gui phppgadmin.
All work perfect, so i can connect to database.
The problem is that when i used to insert data from the phppgadmin interface, it returns some errors while the insert command works perfectly from the command prompt.

Any ideas about the problem?

Thanks in advance

Konstantinos

---

### Post by shufla on 2007-04-24
Hello,

Enable PHP logging and check its contents while having errors (you haven't written what they are, some errors is not enough details).

Also check if memory limits aren't to restricted in php.ini file (if your inserts are big).

Bye,
Shufla

---

