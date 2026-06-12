---
title: "OpenLDAP authentication"
date: 2009-09-22
forum: Server Platforms
---

### Post by xMaximex on 2009-09-22
Hi

I configured my 2 tests server as LDAP server. Both servers replicate between them.

I used this guide:
[https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html)

I tried to authenticate on the server using an account from LDAP (say maxime). I can log on but there's a problem.. It logs me on with administrator account.

```
login as: maxime
maxime@10.0.1.41's password:
Linux vmlinux01 2.6.28-15-server #49-Ubuntu SMP Tue Aug 18 19:30:06 UTC 2009 i686

Last login: Tue Sep 22 14:40:39 2009 from 10.0.1.212
administrator@vmlinux01:~$ whoami
administrator
administrator@vmlinux01:~$ pwd
/home/maxime
administrator@vmlinux01:~$
```

Any help ?

Edit:
/var/log/auth.log when I log on using maxime LDAP account
```
Sep 22 20:45:24 vmlinux01 sshd[18417]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=10.8.0.10  user=maxime
Sep 22 20:45:24 vmlinux01 sshd[18417]: Accepted password for maxime from 10.8.0.10 port 54996 ssh2
Sep 22 20:45:24 vmlinux01 sshd[18417]: pam_unix(sshd:session): session opened for user maxime by (uid=0)
```

---

### Post by xMaximex on 2009-09-22
I found the problem...

user maxime and administrator had the same uid..

---

