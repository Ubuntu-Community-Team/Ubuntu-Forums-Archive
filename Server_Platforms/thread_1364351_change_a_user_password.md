---
title: "change a user password"
date: 2009-12-25
forum: Server Platforms
---

### Post by Vegan on 2009-12-25
OK given a machine with a boatload of users, lts say a user needs to change their password. What can that user do?

also with a new user, can a 1 time password be used so when they log in they are forced to change it?

i am assuming that the user may not have su access

---

### Post by Bachstelze on 2009-12-25
> **Vegan said:**
> OK given a machine with a boatload of users, lts say a user needs to change their password. What can that user do?

A user can change his own password with the [font=monospace]passwd[/font] command (if allowed by the system's settings). When a user is forced to change his password, he will be prompted for it at next login before he can do anything else.

> **Vegan said:**
> also with a new user, can a 1 time password be used so when they log in they are forced to change it?

After creating the account:

```
sudo chage -d 0 username
```

---

### Post by Vegan on 2009-12-25
Thanks

---

