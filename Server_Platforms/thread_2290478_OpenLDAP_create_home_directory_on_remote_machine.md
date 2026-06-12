---
title: "OpenLDAP create home directory on remote machine"
date: 2015-08-12
forum: Server Platforms
---

### Post by dmytro2 on 2015-08-12
Hi everyone) I'm trying to setup ldap so that leap server is deployed on one machine with Ubuntu and home directories with users are created automatically on other machine with Ubuntu when entry is added to leap db. So I have two questions:
- how can I set up ldap so that users are created automatically on entry addition? 
- how can I make ldP create users on remote machine on entry addition?
Thanks)

---

### Post by TheFu on 2015-08-12
Almost anything can be scripted. Create a script that does the LDAP and creates the user HOMEs as you like.

I searched for "*leap server ubuntu*" and didn't find anything relevant.

---

