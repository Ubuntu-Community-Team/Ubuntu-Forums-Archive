---
title: "ldap clinet pam dont work"
date: 2008-08-12
forum: Server Platforms
---

### Post by mattiashem on 2008-08-12
Hello!


Using one openldap server as central users mangemnet.
Have work nice with ubuntu 7.10.

But when a upgrade to 8.04 the clients cant connect to the server anymore

If i tried login 
the first time a efter a wrong password an *** you can se the server repliyed login incorrect but the second tine a enterd the right password and then a gets back to root login



[SIZE="2"]root@skalman:/var/log# login
skalman login: mattias
Password:

Login incorrect
skalman login: mattias
Password:
root@skalman:/var/log# [/SIZE]

If a then tried to login using ssh 
a onlyt gets wrong password,

[SIZE="2"]Aug 11 22:03:42 skalman login[9352]: pam_ldap: error trying to bind as user "uid=mattias,ou=People,dc=skole,dc=skolelinux,dc=no" (Invalid credentials)
Aug 11 22:03:42 skalman login[9352]: pam_unix(login:auth): check pass; user unknown
Aug 11 22:03:42 skalman login[9352]: pam_unix(login:auth): authentication failure; logname=mat uid=0 euid=0 tty=pts/0 ruser= rhost=
Aug 11 22:03:44 skalman login[9352]: FAILED LOGIN (1) on 'pts/0' FOR `UNKNOWN', User not known to the underlying authentication module[/SIZE]

Here is the auth.log 

As you can se when a enter mattis the fist time the password was wrong and there fore ldap complains Invalid credentials,
The other lines are from then i tried to loggin using ssh.

any ides ??

// matte

---

