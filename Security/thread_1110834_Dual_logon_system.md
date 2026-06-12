---
title: "Dual logon system"
date: 2009-03-30
forum: Security
---

### Post by netlander on 2009-03-30
Hi All,

I'm implementing a high security system, and I need the system to request two different passwords in order to grant access.

The idea is having a user in the system with two different passwords and the logon has to be with both passwords at the time.

Can anyone give a hint on this?

Thanks and regards

---

### Post by lemming465 on 2009-03-31
You should be able to get the effect you want by adding appropriate [pam_userdb]("file:///usr/share/doc/libpam-doc/html/sag-pam_userdb.html") lines to /etc/pam.d/common-auth and /etc/pam.d/common-passwd. 

However, if you really want high security, you should be thinking multifactor authentication, with fingerprints, or RSA secureid tokens, or smartcards, or USB crypto tokens like Aladdin sells, or whatever.  Bank ATM machines require something you have (debit card) and something you know (PIN code); if possible you should too.

---

