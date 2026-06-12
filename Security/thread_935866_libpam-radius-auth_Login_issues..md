---
title: "libpam-radius-auth Login issues."
date: 2008-10-02
forum: Security
---

### Post by jreige on 2008-10-02
Hi Everyone,
I am trying to configure system authentication using PAM against a radius server.  I have installed libpam-radius-pam on the system and have configured the system exactly like I have configured the CentOS box we have in the environment.  The CentOS box PAM authentication off our radius server works well.  

I have created an account in the /etc/passwd, same username as the radius account.  I have done this on the CentOS box and it works fine.  When I attempt to login using SSH or anything else for that man, the /var/log/auth.log indicates that the password is incorrect.  

passwd -S <username> indicates that the local account is Locked.  I unlocked and a random password is applied.  Still no go.  

Anyone seen this issue?  The problem is not the radius server as i have this working on a CentOS system.

System information
Ubuntu Feisty on i386.

---

### Post by wuhaa on 2009-02-12
Hi,

I'm trying to do exactly that with centos too. Can you help me in setting that up in centos? I'm using centos 5.2..

I want to have the radius box separate from the ssh box so I can add multiple ssh boxes as need grows.

Thanks,

---

