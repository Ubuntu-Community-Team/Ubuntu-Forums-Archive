---
title: "server help"
date: 2006-07-16
forum: Server Platforms
---

### Post by martymart on 2006-07-16
Hi all,
I want to install a server that verifies user logins and determines what files they can access like active directory. How can I achieve this with linux/ubuntu.

Thanks for your time,

Martin

---

### Post by Randomskk on 2006-07-16
Would FTP work?

---

### Post by martymart on 2006-07-16
No, I was thinking about something that verifies logon to systems like at work.

---

### Post by dustparticle on 2006-07-16
> **martymart said:**
> Hi all,
I want to install a server that verifies user logins and determines what files they can access like active directory. How can I achieve this with linux/ubuntu.

Thanks for your time,

Martin

Take a look at Samba.

[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

---

### Post by martymart on 2006-07-16
Does samba provide active directory type services and does it provide the linux equilalent. Am I better off using linux specific tools like cups and NFS?

---

### Post by datakid on 2006-07-18
well, talk about opening a can of worms.

1. Samba version 3.x (current stable) cannot do AD by itself. The next version of Samba will be able to though.

2. The bits missing are something like: kerberos, ldap and something else. These can be and have been replaced by openldap + (kerberos replacement here). There is a modicum of documentation if you go looking. google groups is a good place to start.

3. Of course, it depends exactly what you want - if you want a PDC, then Samba can do that - the profiles and login credentials can all reside on a linux server and all the windows clients can authenticate against it, using smbpasswd, tbpasswd, ldap and otehrs. CUPS is also integrated into samba. BUT this option doesn't allow other things, like group policies, SUS (or WSUS) and the like. It can also do group and user access, like any linux box can, and this is applied to any shared folders on said samba server.

4. NFS is another option, but again, would require reading a lot, sinceI know little about it :)

hence, I would say yes, samba does what you need.

there is a great walkthrough here:

[http://www.howtoforge.com/samba_setup_ubuntu_5.10_p4](http://www.howtoforge.com/samba_setup_ubuntu_5.10_p4)

---

