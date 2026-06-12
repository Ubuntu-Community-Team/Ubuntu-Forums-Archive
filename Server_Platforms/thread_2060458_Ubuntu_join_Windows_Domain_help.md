---
title: "Ubuntu join Windows Domain help"
date: 2012-09-20
forum: Server Platforms
---

### Post by scarrez on 2012-09-20
Hi,

I'm running Ubuntu 10.04.4 LTS and Windows Server 2008 R2.

I'm trying to join the Ubuntu server to the windows domain.
I have followed many tutorials including...

[http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/](http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/)

Several others to do with samba/kerb.

At the current moment the command I'm trying to use which has had the most success is;

*net ads join -U systemadmin*

**Resulting in...**
*kerberos_kinit_password [email]UBUNTU@DOMAIN_CENSOR.LOCAL[/email] failed: preauthentication failed*

I'm 100% sure I'm using the right username/password.

Any help is much appreciated,
Scarrez

---

### Post by albandy on 2012-09-20
> **scarrez said:**
> Hi,

I'm running Ubuntu 10.04.4 LTS and Windows Server 2008 R2.

I'm trying to join the Ubuntu server to the windows domain.
I have followed many tutorials including...

[http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/](http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/)

Several others to do with samba/kerb.

At the current moment the command I'm trying to use which has had the most success is;

*net ads join -U systemadmin*

**Resulting in...**
*kerberos_kinit_password [email]UBUNTU@DOMAIN_CENSOR.LOCAL[/email] failed: preauthentication failed*

I'm 100% sure I'm using the right username/password.

Any help is much appreciated,
Scarrez

Are you using net ads join with likewise ? You shouldn't as these are different ways of doing the same but using different software.

Probably you have modified samba configuration, and kerberos, ... With likewise-open you don't need to do that, simply install it and run:

sudo domainjoin-cli join domain.extension user_with_domain_privileges

or in a graphical way going to System --> Administration --> Active Directory Membership.

---

### Post by scarrez on 2012-09-21
Hi,

I have been using multiple VM's when trying different methods to avoid the issue you mentioned.

Thanks for the reply
Scarrez

---

### Post by Bongcs on 2013-04-18
While joining to windows server 2003 from ubuntu using likewise open5 gui

I am getting the following error:

Lsass Error, DNS_ERROR_BAD_PACKET

even thou i have add DNS server role to windows server.

Please guide .

Regards,

Bongcs.

---

