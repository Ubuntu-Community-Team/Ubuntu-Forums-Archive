---
title: "Can't get ubuntu client to require password change when Centos-DS requires it."
date: 2010-10-15
forum: Server Platforms
---

### Post by rmainard on 2010-10-15
Hello,

I am running ubuntu 10.04 64 bit with Centos Directory Server as my centralized authentication tool. I can log in just fine with my ubuntu client, however when go to my Directory Server and tell it to require a password change on reset for any of my users, the ubuntu client doesn't require the user to reset their password. the reason I need this to work is so I can reset a users password from the Directory server and then have it use what I set it to for their next login attempt but then require them to set their own password. After days of searching I have only found out that it can be done by setting the option in Directory Server but Ubuntu 10.04 seems to just ignore the option. I am using the libnss-ldapd and libpam-ldapd packages on the Ubuntu client because the libnss-ldap and libpam-ldap didn't work at all, what am I missing? Please Please Please Please help! Thanks

---

### Post by Linux2Man on 2011-03-29
I'm using CentOS DS and Ubuntu 10.10, user login successfully but cannot change his password

---

