---
title: "slappasswd  is a sodu password or a different than it."
date: 2012-08-12
forum: Server Platforms
---

### Post by honey_bee on 2012-08-12
i am using Ubuntu server 1st time to configure openldap. The thing which I want to discuss is that the "slappasswd" is the password of the root user or it will be the password for only  the openldap server it self. Can I give a different password than my root user i.e sudo or it  is same my sudo password ?

thanks.
honey

---

### Post by kennethconn on 2012-08-12
When you were installing/setting up the openldap server you were asked to provide a password for administering the server. This is what I think you are looking for.
slappasswd is a utility, check the man pages for more.

---

### Post by honey_bee on 2012-08-12
Thanks for the reply. Well during installation it ask to administrator password which ubuntu normally ask to install any software package. slappasswd is the same one ? or we can give a new one which is different from our system while administrator password.
I have also checked the man page but still it does not explain wich actually i am asking.

Suppose my ubuntu sudo password is :- 123456
so the slappasswd can be different if i want like:-   smith123

I does not know that practically it is correct or not  any ubuntu user who have configured openldap in his server may guide me about my confusion .

thanks
honey

---

### Post by kennethconn on 2012-08-12
Did you read the guide?
[https://help.ubuntu.com/12.04/serverguide/openldap-server.html#openldap-server-installation](https://help.ubuntu.com/12.04/serverguide/openldap-server.html#openldap-server-installation)
 
I think it should clear things up for you.
 
When you talk about sudo or root user (well what I think you are referring to) that is all do do with the Ubuntu server (think local machine, it just so happens to be a server). When you install OpenLDAP on your Ubuntu server, it is a completely different set of accounts and passwords.
 
slappasswd is a utility used for generating encoded password strings so that you can place that in files instead of the actual password (not sure if it does more than that but you can read the man pages to find out more).
 
Always read up as much as you can before you install, it is best practice (often ignored by many).

---

