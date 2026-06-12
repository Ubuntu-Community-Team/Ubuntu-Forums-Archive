---
title: "Likewise-Open joins AD but doesn't create computer account"
date: 2008-07-15
forum: Server Platforms
---

### Post by dustinfl on 2008-07-15
I'm trying to get a JeOS (8.04.1) virtualized server joined to Active Directory, and running "domainjoin-cli --log . join ourdomain administrator" does indeed join the system to our domain (verified by being able to authenticate via domain\user with ssh), the computer account is not created in the "Computers" CN, which it is suppose to do by default. The command does spit out the following, which perhaps relates to why the computer account is not being created:

20080715113412:WARNING:Short domain name not specified. Defaulting to 'ourdomain'
20080715113413:WARNING:Unable to find pam_lwipasspolicy
20080715113413:WARNING:Unable to find pam_lwipasspolicy

Does anyone have any clues? Thank you! :)

---

### Post by dustinfl on 2008-07-15
Actually, let's put a hold on this. I found out that a computer account was indeed created, but it wasn't synchronized to other Domain Controllers, thus we're having a bigger problem. I'll update the thread when we resolve it, but that's most likely the problem.

---

