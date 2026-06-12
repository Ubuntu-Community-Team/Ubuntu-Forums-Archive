---
title: "dovecot authdb"
date: 2012-01-14
forum: Server Platforms
---

### Post by Jesse Degger on 2012-01-14
Hi all,

I'm having some trouble with my dovecot configuration.

Currently I'm running dovecot in combination with postfix. I'd like to have userauth mysql database so I can manage it easily. 

Unfortunately, it wont work. I'm getting this error:

```
$ sudo doveadm auth test
Password: 
doveadm(root): Fatal: Couldn't connect to auth socket

```I'm running Ubuntu server 11.10. Dovecot and postfix are installed via Webmin.

Does anyone have a solution for this problem?


Kind regards,

Jesse Degger

---

