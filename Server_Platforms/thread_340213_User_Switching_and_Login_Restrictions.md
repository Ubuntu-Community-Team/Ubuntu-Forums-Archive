---
title: "User Switching and Login Restrictions"
date: 2007-01-16
forum: Server Platforms
---

### Post by jimarko on 2007-01-16
Hi All,

I'm looking to set up a user account which cannot be logged onto at the login prompt, but can be logged onto using 'su *<username>*' from other accounts.

Is it possible to apply a rule to that account to block login access from a console, only allowing access via 'su'?


The reason I want to do this is so that I can create a better auditing path in our event logs, as we'll be able to see who 'su's from their account to this other account.


Thanks,
James

---

### Post by kidders on 2007-01-16
Hi there,

If you don't provide an account with a password, nobody will be able to use it to log in. User accounts for postfix & apache are common examples ... you can run commands as these users (eg with cron, etc.), but trying to log in by typing "www-data" at a "Username:" prompt won't get you very far.

Hopefully that's what you're after. :-)

---

### Post by PetePete on 2007-01-17
you could change that accounts shell to /dev/null i suppose (in /etc/passwd), think that would work?

i'm presuming you mean logins through ssh ?
well in the ssh_config file you could add
DenyGroups nameOfGroup

then just create nameOfGroup and add the denied remote login user to it.

---

### Post by kidders on 2007-01-17
> **PetePete said:**
> you could change that accounts shell to /dev/null i suppose (in /etc/passwd), think that would work?

i'm presuming you mean logins through ssh ?
well in the ssh_config file you could add
DenyGroups nameOfGroup

then just create nameOfGroup and add the denied remote login user to it.

The snag with these suggestions is that they don't actually prevent logins ... they only prevent access to a terminal, which is not quite the same thing. Depending on jimarko's requirements of course, they may be perfectly suitable. :-)

---

