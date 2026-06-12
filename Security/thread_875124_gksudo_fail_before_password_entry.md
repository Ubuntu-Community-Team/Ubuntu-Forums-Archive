---
title: "gksudo fail before password entry?"
date: 2008-07-30
forum: Security
---

### Post by PaladinOfKaos on 2008-07-30
I've got an account setup that is not a member of the 'admin' group, so both sudo and gksudo fail when that account tries to use them. That works fine.

The problem is with gksudo - it still asks for a password, then gives a rather cryptic (for a new user) error message.

I was wondering if there's an easy way (short of rebuilding gksudo from source) to make gksudo fail with a nicer dialog before the password prompt.

Thanks,
Branan

---

