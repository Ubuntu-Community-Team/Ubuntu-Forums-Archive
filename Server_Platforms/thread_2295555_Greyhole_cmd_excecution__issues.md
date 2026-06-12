---
title: "Greyhole cmd excecution  issues"
date: 2015-09-19
forum: Server Platforms
---

### Post by declan4 on 2015-09-19
Hi, I get the below when issueing any command with greyhole.
I recently upgraded to samba4 and ubuntu 14.2.
access to the mysql dbase works from windows client.
I have since upgraded to ubuntu 14.4

Has anybody nay idea? would really appreciate some help here.

/ Declan

$ sudo greyhole -s
ERROR: Can't connect to database: could not find driver

---

### Post by gboudreau on 2015-09-20
Look like you're missing either php5-mysql or php5-mysqlnd package, or they are somehow disabled in your PHP configuration.

---

### Post by declan4 on 2015-09-23
Thanks gboudreau for the quick reply!
I hadn't seen that greyhole was dependent on php5. I'll try that and report back.

---

### Post by declan4 on 2015-10-03
This was indeed the problem, thanks. I have now stumbled upon another problem but I will take in a new thread.
/Dec

---

