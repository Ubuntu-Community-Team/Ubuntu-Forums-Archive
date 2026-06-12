---
title: "Block user from shared folder"
date: 2008-12-02
forum: Security
---

### Post by piratebill on 2008-12-02
Hi everyone, I have a question about ubuntu server.  Currently, I have about 5 user accounts (all with private home folders) and one shared directory that everyone has access to.  To make a long story short, I need to give some classmates server access, however I do not want them to be able to access that shared directory.  How can I prevent this?

---

### Post by cdenley on 2008-12-02
> **piratebill said:**
> Hi everyone, I have a question about ubuntu server.  Currently, I have about 5 user accounts (all with private home folders) and one shared directory that everyone has access to.  To make a long story short, I need to give some classmates server access, however I do not want them to be able to access that shared directory.  How can I prevent this?

By server access, do you mean access files remotely? If so, what service will they use for file access? If you don't want user's to be able to access the directory, then why is it a "shared" directory? Who does need to access it?

---

### Post by piratebill on 2008-12-02
Sorry if I was not clear.  As of now, there are 5 accounts that need access to that directory.  I want to add another account that does not have access.  

right now its only ssh access.  This new account will be used to work with mysql and other services.  The new user will need ssh to tunnel into my server (because the router is set to only forward ssh traffic). I just dont want them to be able to access certain files.



EDIT:
the directory in question currently has permission settings set at 777.  Can I set some kind of group settings on the directory to restrict just one user?

---

### Post by bodhi.zazen on 2008-12-02
Make a new group, call it what you will, say foo

Make the directory owned by root.foo with permissions of 770

Place the 5 users in the group foo.

---

### Post by piratebill on 2008-12-02
bodhi.zazen, thank you so much.  I have created a new group, but how do I add users to it?


Edit:
found it:

"# usermod -a -G ftp tony"

---

