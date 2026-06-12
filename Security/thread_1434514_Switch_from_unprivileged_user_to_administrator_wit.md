---
title: "Switch from unprivileged user to administrator without password possible"
date: 2010-03-20
forum: Security
---

### Post by Interruptor on 2010-03-20
Create new user, select "Unprivileged" type.
Switch to new user without logging out from old.
Try to shut down/restart and cancel password request.
You will switch to old user without any password needed.

---

### Post by DawieS on 2010-03-20
I fail to see any security implications. If you end up as "old user", that is where you started from, nothing gained..? Please elaborate if I have a misunderstanding.

In any case, if you have physical access to a machine, you have total control.

---

### Post by adam814 on 2010-03-21
If I were creating a new user for someone else I would log out before having them log in.  Of course if you simply switch users on the command line and authenticate as the new user you can "get back" to your old user.  All you have to do is logout as the new user.  The only security risk I see is for some kind of social engineering where an admin gets talked into doing just what you've described, but in my opinion those who don't know better shouldn't be admins for any production system.

---

