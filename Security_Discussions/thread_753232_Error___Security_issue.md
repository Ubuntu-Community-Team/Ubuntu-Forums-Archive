---
title: "Error:   Security issue?"
date: 2008-04-12
forum: Security Discussions
---

### Post by MeTylerDurden on 2008-04-12
I get this message when opening synaptic package manager , ::
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This wants me to run "    dpkg --configure -a  "   andj then enter superpassword ..  so does that mean my password..     and is it safe to proceed?:popcorn:

  The Liberator who destroyed my property has realigned my perception

---

### Post by The Tronyx on 2008-04-12
> **MeTylerDurden said:**
> so does that mean my password..     and is it safe to proceed?

That is correct sir :)

---

### Post by MeTylerDurden on 2008-04-12
After I run sail command in (terminal?)  i get this  answer: requested operation requires superuser privilege   ... I enter my password and nothing  , i get this:
bash: metyler: event not found

---

### Post by MeTylerDurden on 2008-04-12
I found this  and it works...    code:

sudo dpkg --configure -a


  thanks

---

### Post by hyper_ch on 2008-04-12
yeah, the default error messages don't take in account that Ubuntu uses sudo and not superuser itself.

---

