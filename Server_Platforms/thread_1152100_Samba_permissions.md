---
title: "Samba permissions"
date: 2009-05-07
forum: Server Platforms
---

### Post by artheus on 2009-05-07
Hey!

I've got a small problem with samba.
I've gotten it to work so that I can browse the folder /mnt/sdb1 by writing

```

[export]
    comment = my data
    path = /mnt/sdb1/
    browseable = yes
    guest ok = no
    read only = no

```

And sure.. I can browse the folder through network.. BUT! I can't write to it. The folders in it and stuff are owned by another user.. but the user I log in with should override all of those permissions.

How do I do that? (I can't make the user I use to log in, the owner of the folder, cause that'll ruin alot of other stuff)

Cheers,
Artheus

---

### Post by a9k3d on 2009-05-14
You have a unix permissions problem. I suspect your only solution is to put both users in the same group and set the group and group permissions of those files you want to shared by both.

---

### Post by uzi09 on 2009-05-15
> **a9k3d said:**
> You have a unix permissions problem. I suspect your only solution is to put both users in the same group and set the group and group permissions of those files you want to shared by both.

Agreed. If we can get an output of your ls -l of that directory, it should be verify the claim

---

