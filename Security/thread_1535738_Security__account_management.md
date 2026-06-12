---
title: "Security / account management"
date: 2010-07-21
forum: Security
---

### Post by baguahsing on 2010-07-21
I am new to linux and Ubuntu. I am the sole user of a laptop. When I installed linux I created 2 accounts, one with admin privs and one without. Philosophy, the admin account would manage and update the system, the other account was for everyday use. Following bodhi.zazen's security sticky, I activated apparmor for firefox. Does this action apply globally to all accounts? I tried to activate apparmor for the non-admin account and was told it wasn't listed as a sudo user. If I add the non-admin account to the sudo user list haven't I just given it admin privs? I thought that by cruising the internet with the non-admin account that if I stumbled across a virus or malware that my computer would be "safe" because that account does not have root / admin privs. I guess I don't really understand how linux is setup and the relationship between root, admin, and non-admin privs.

---

### Post by bodhi.zazen on 2010-07-21
> **baguahsing said:**
> I am new to linux and Ubuntu. I am the sole user of a laptop. When I installed linux I created 2 accounts, one with admin privs and one without. Philosophy, the admin account would manage and update the system, the other account was for everyday use. Following bodhi.zazen's security sticky, I activated apparmor for firefox. Does this action apply globally to all accounts? I tried to activate apparmor for the non-admin account and was told it wasn't listed as a sudo user. If I add the non-admin account to the sudo user list haven't I just given it admin privs? I thought that by cruising the internet with the non-admin account that if I stumbled across a virus or malware that my computer would be "safe" because that account does not have root / admin privs. I guess I don't really understand how linux is setup and the relationship between root, admin, and non-admin privs.

Many of your questions can be answered here :

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

The "Admin" account on Ubuntu is not the same at all as the admin account on Windows.

On Ubuntu, the equivalent of a Windows Administrative account is root.

On Ubuntu , and Admin account is in the admin group and has access to the root account via sudo. So you are already running a limited account. The account does have access to root via a password.

On Windows an Admin account has full system access without a password.

So while some people with the "Windows Mentality" have created additional accounts for security reasons, IMO, this adds very little if anything to your overall security.

Otherwise the rootsudo link will show you how sudo works in a little more detail.

This is why we discourage disabling the password for sudo. So long as you do not deactivate security features you should be good to go without the need for an additional account for "daily use".

---

### Post by baguahsing on 2010-07-21
Thanks for the reply.  I will definitely look at the link.  If I was not the only user on the computer and I went in under the admin account and activated apparmor for firefox, would apparmor protect all users or would I have to configure it for each user?

---

### Post by bodhi.zazen on 2010-07-21
> **baguahsing said:**
> Thanks for the reply.  I will definitely look at the link.  If I was not the only user on the computer and I went in under the admin account and activated apparmor for firefox, would apparmor protect all users or would I have to configure it for each user?

If you activate the firefox profile as an admin user it applies to all users on the system.

---

