---
title: "MYSQL flush privileges locks out root"
date: 2013-03-21
forum: Server Platforms
---

### Post by Darghon on 2013-03-21
Hi all,

I've noticed on several occasions when I execute some sql statements like "grant privileges on something.* to user@localhost;" with or without the identified by parts.
the user rights don't take effect.
Once I do a flush privileges, it does work, but the root account gets locked out...

I remain logged in, and can set my password before closing the session, which saved the account.
But if I don't, the system tells me on the next login that my password is incorrect...

Anyone have any idea why?

thx

---

