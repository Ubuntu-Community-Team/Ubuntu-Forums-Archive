---
title: "sssd/nslcd help"
date: 2022-03-08
forum: Server Platforms
---

### Post by kevdog on 2022-03-08
High I'm trying to configure a system that uses sssd or nslcd to use a ldap implementation with pam module for authentication.  I'm having a hard time trying trying to configure the pam modules since I'd ideally like the ldap lookup to be confined to users with uid>1000 or uid>(limit) so it doesn't interfere with local users of the system.  I'm not sure how to configure the pam.d modules for this.

---

### Post by TheFu on 2022-03-08
I've never used sssd. Never attempted to connect to MS-AD, so I didn't see the need.

[https://help.ubuntu.com/community/SingleSignOn](https://help.ubuntu.com/community/SingleSignOn) seems to cover LDAP use.  Last time I setup SSO, I didn't use Kerberos or SSSD. It worked fine with normal PAM config stuff.  I'll look for my notes, but cannot promise anything. It has been since 2013, I think.

---

### Post by kevdog on 2022-03-09
@TheFu -- I perused the document.  I didn't find anything related to what I was maybe attempting to do unfortunately.  I have sssd actually setup and running but just not with the access restriction of UID>(certain number).

---

### Post by TheFu on 2022-03-09
Don't know if any of this is helpful.

For Unix systems, the POSIX LDAP schema is required. This would convert those UUID-like user/group-ids and translate into POSIX userids and groupid, as expected.

But I haven't looked at this stuff too recent.  For login authentication support on my Unix/Linux client systems, only pam settings needed to be modified. I didn't find my LDAP notes, sorry.

---

### Post by kevdog on 2022-03-09
Hey thanks for your help

---

