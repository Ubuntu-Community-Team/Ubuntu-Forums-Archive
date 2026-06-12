---
title: "/etc/shadow, root wasn't disabled!"
date: 2009-10-06
forum: Security
---

### Post by jessiebrownjr on 2009-10-06
Hey guys.. I did a cat /etc/shadow and my root UN had a password activated, not a ! like my desktop does.

Now once upon a time I played with it in system/admin/users and groups, but it seemed to fake like it was letting me enable it, then it didn't *stick*...

would that have put a password there?  I gedit'ed it back to ! and reset, and it is still "disabled" now..

Kinda worried now, any advice :-)?

---

### Post by cdenley on 2009-10-06
> **jessiebrownjr said:**
> Hey guys.. I did a cat /etc/shadow and my root UN had a password activated, not a ! like my desktop does.

Now once upon a time I played with it in system/admin/users and groups, but it seemed to fake like it was letting me enable it, then it didn't *stick*...

would that have put a password there?  I gedit'ed it back to ! and reset, and it is still "disabled" now..

Kinda worried now, any advice :-)?

Was there a password hash set, or was it blank? How exactly did you attempt to enable it before?

---

### Post by jessiebrownjr on 2009-10-11
> **cdenley said:**
> Was there a password hash set, or was it blank? How exactly did you attempt to enable it before?
system>admin>user/groups
There was a hash, I removed it with ! and its fixt and gone.

---

