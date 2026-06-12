---
title: "htdigest + Ubuntu 10.10 Problem"
date: 2010-12-12
forum: Server Platforms
---

### Post by zemon_ on 2010-12-12
On other editions of ubuntu server I had no problem saving multiple users and passwords with htdigest but now it seems it is only possible to save one user and password.

```
sudo htdigest -c /etc/apache2/passwords directory user
```

When I add a second username and password for the same directory it overwrites the first.

Can anyone help me with this issue?

---

### Post by zemon_ on 2010-12-12
The problem is I was using the -c when creating the second user and password, which was deleting the password file and creating new.

The second user and password should be created like.

```
sudo htdigest /etc/apache2/passwords directory user
```

---

