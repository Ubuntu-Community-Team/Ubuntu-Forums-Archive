---
title: "Preventing su TO certain accounts"
date: 2013-03-25
forum: Security
---

### Post by joelg90 on 2013-03-25
I built an xubuntu 12.04 box in our DMZ/secondary ISP for disaster recovery purposes if our main network goes down.

Because of that, I only allow one user account to ssh in, then dump that account straight to a python script that handles su-ing to another less secured user. The python script is basically just trying to hide any useful information someone might glean.

In the event of a disaster, the monkey putting out fires will have to remember the password, or have it written down. Writing down a password almost entirely defeats the purpose. So need a not-so-secure password.

I know you can set su/sudo group permissions, which I have done; but can you prevent accounts from being su-ed TO?

I would like a "local only" account that is not allowed via SSH access, nor allowed to be switched to by another user.

I've searched superuser.com and here, but "disable/restrict su" doesn't come up with my desire.

---

