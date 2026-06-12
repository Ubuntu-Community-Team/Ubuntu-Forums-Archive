---
title: "Some tricky user permissions and settings"
date: 2008-08-01
forum: Security
---

### Post by technomaniac on 2008-08-01
We have installed ubuntu hardy on all college PCs. The authentication is done via NIS. We need to do the following things:

1. disable sudo for all students. They are not supposed to run anything as root

2.Enable Compiz and Emerald themes by default on all users. And set a default Compiz and Emerald themes.

Help is deeply sought

---

### Post by vanadium on 2008-08-01
By default, new users you add to an Ubuntu system have no root privileges.

With respect to how an account looks: I believe there exists a "template" for that, i.e. a default profile that is used for new users, which you could adapt, but I do not know the details.

---

### Post by unutbu on 2008-08-01
Check out /etc/skel. Anything you put there will be copied into each new user's account when the account is created. So create one user, set up compiz and emerald, then copy the extra dot config files into /etc/skel.

---

### Post by technomaniac on 2008-08-02
Thanks a lot...Got it

---

