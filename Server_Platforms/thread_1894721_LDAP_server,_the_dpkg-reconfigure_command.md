---
title: "LDAP server, the dpkg-reconfigure command"
date: 2011-12-13
forum: Server Platforms
---

### Post by xMusic on 2011-12-13
Hi, 
I'm running a ubuntu 10.04 on a virtual machine and I'm trying to make an openLDAP server work

I am always having the same problem which stops me from adding my .ldif into my LDAP server.

the "sudo dpkg-reconfigure slapd" wont let me change the password and the main domain, it only ask me 3 things which are:

Do I want to ommit the openLDAP configuration <- no
Do I want to delete the database when packet is purged <- yes
Should I allow the LDAPV2 protocol <- no

Beside that nothing is asked to me so I can't configure the password, hence i can't add any file into the server.

help me please

ps: the slappasswd command doesnt work when I am asked for LDAP password either

---

### Post by maverickaddicted on 2011-12-14
If you are using openldap 2.3, then check out these

[http://www.howtoforge.com/forums/showthread.php?t=42236](http://www.howtoforge.com/forums/showthread.php?t=42236)
[http://www.adac-solutions.com/?p=33](http://www.adac-solutions.com/?p=33)

---

