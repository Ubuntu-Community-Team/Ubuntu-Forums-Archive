---
title: "mySQL directory permissions"
date: 2009-03-10
forum: Server Platforms
---

### Post by crokett on 2009-03-10
I have a problem and am not sure there is a way out.  I try to get to the database with mysqladmin command and am told that the machine with my IP Address is not allowed to connect.  So I try it directly from the server and I am told that 'user@local is not allowed to connect to this database'.

How can I get to the database to configure access if I can't get to it from anywhere?  I tried removing and reinstalling thinking I'd be prompted for something, but that didn't happen.

---

### Post by hyper_ch on 2009-03-10
when you installed mysql didn't it ask for a root passwort to be added?

---

### Post by crokett on 2009-03-10
Yes but I very cleverly told it no root access allowed.   Then it prompted me for a username, I gave it a username and password but I can't access the database.

I can run 'mysql -u <username> and get the msql> prompt but if I try either 'use mysql' or 'use ibdata1' I get the 'access denied for user@localhost' error.  I think I screwed something up somewhere.

I tried removing and reinstalling via apt-get since this is a brand new setup but wasn't prompted for any user info the 2nd time around and I still had the same problem.  I don't mind reinstalling if that is the fix, I just need it to do a clean install.

---

### Post by hyper_ch on 2009-03-10
restart mysql in "recovery" mode so that you can access it without password. Google should provide the answer on how to do that.

---

### Post by crokett on 2009-03-10
I fixed it.   Thanks for the help.

---

