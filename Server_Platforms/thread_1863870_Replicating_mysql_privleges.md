---
title: "Replicating mysql privleges"
date: 2011-10-18
forum: Server Platforms
---

### Post by bigmonmulgrew on 2011-10-18
Hi
I'm experimenting with replication in mysql
I'm working on 2 ubuntu servers both 11.04 one a VM running on ubuntu server the other is a vm running on Virtual box in windows 7
I've setup database replication through phpmyadmin
This works fine, the databases are copied over fine.

However the users and privleges are not copied so if I create a new user on the master I have to manually create it on the slave.
Is there a way to replicate the users as well as the databases

---

### Post by bigmonmulgrew on 2011-10-18
OK I have found using php my admins synchronize page I can copy all the users over at once and its pretty straight forward to do but I'd still like it to be automated like replicating tables is

---

### Post by bigmonmulgrew on 2011-10-19
ok using that method breaks replication and I cant fix it so I'm back to doing it one user at a time manually

---

