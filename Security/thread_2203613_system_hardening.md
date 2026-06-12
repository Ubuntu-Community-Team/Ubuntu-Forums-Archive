---
title: "system hardening"
date: 2014-02-04
forum: Security
---

### Post by cbillson on 2014-02-04
Hi, wonder if anyone could assist, I'm concerned I'm likely to lock myself out :D

I have an Ubuntu box which mostly runs a single application, which runs under root. a number of folders and logs are created as the root user.

I want to ensure that users that have the ability to create files, cannot create files they can then execute.

Firstly i need to restrict access to chmod - assume this is the same as restricting access to su (which i did via a group)

Then i need to set the umask for users to a level where they can read and write files they create, but not execute them - umask 177 ?

Lastly, i want to ensure that the root user can still create files as it does now. 

My confusion.. it appears users and root run a different umask? if this is the case, i can see that one of them is set in /etc/login.defs but how do i ensure i only amend the users, leaving root as it is currently?

Any advice appreciated, cheers

---

