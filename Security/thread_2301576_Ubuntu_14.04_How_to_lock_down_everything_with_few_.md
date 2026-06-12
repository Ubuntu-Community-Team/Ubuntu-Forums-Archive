---
title: "Ubuntu 14.04 How to lock down everything with few exceptions?"
date: 2015-11-03
forum: Security
---

### Post by jbiddenback0617 on 2015-11-03
We're setting up a laptop with Ubuntu, and the 6 year old (against my better judgement) is allowed to use it.  He may use YouTube, a few games, and nothing else.  We want deny access to everything except a few shortcuts placed on the desktop.  I'm sure this is going to involve putting him on his own account (or a guest account) and changing permissions, but I'm not sure where exactly to start with the permissions change.

Help please?

---

### Post by TheFu on 2015-11-03
For a 6yr old, the security doesn't need to be much. Icons on the desktop using XFCE/LXDE are probably sufficient. Don't think Unity can be used.

If you want to lock down the system for a 10+ yr old, use something like TinyCore and only load the specific applications to be allowed. After all, any application can be installed into a user's HOME, where they would obviously have permissions  to  run  it.

Linux is designed at the core to allow users to run most programs on the system. Trying to stop that is a difficult thing and goes against the core design philosophy of Unix.  Power-to-the-users!

---

