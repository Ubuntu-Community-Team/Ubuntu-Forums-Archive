---
title: "AD migration to linux"
date: 2008-11-18
forum: Server Platforms
---

### Post by kuda on 2008-11-18
Hi all,
I have few servers (members of Active directory domain/exchange/file/printserv. etc) and I would like to migrate them to ubuntu/debian. I would appreciate any kind of advices,experiences,problems. I have read rather much stuff about that but I am thinking about somebody who had success with this operation. I am not sure what kind of tools can one use for migration of accounts, password and settings .... Thanx in advance!

---

### Post by linux_tech on 2008-11-19
To export migrate user password information from Active Directory into an OpenLDAP repository, you may want to use pwdump2 to export as a LDIF file. 
Info how to do this here.
[http://www.fatofthelan.com/articles/articles.php?pid=13](http://www.fatofthelan.com/articles/articles.php?pid=13)

---

