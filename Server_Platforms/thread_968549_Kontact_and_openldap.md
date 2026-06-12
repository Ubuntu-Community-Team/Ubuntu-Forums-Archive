---
title: "Kontact and openldap"
date: 2008-11-02
forum: Server Platforms
---

### Post by brechmos on 2008-11-02
I admit I am reasonably new to openldap but have tried configuring it in the past.  I have a simple address book type of database.  I can get Kontact to show me entries, but it won't let me edit (and update) them.

I don't get an error in Kontact, but it does not update the entry and my syslog has:

Nov  2 19:52:58 ubuntu slapd[23718]: conn=0 fd=15 ACCEPT from IP=192.168.2.13:57041 (IP=0.0.0.0:389) 
Nov  2 19:52:58 ubuntu slapd[23718]: conn=0 op=0 BIND dn="" method=128                               
Nov  2 19:52:58 ubuntu slapd[23718]: conn=0 op=0 RESULT tag=97 err=0 text=                           

I have a bind DN set for the Address Book and the Authentication is "Simple".  I can do searches and they work out fine.  So, I am assuming the problem is the lack of an entry for the BIND dn in the log.    Any ideas of things I can check?  I am not sure if it is a Kontact issue or openldap configuration problem.

I am using Ubuntu 8.10 (Kontact v1.3 and openldap 2.4.9, all stock stuff).

---

