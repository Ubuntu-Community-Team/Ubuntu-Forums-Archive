---
title: "regular users cannot logout"
date: 2010-12-22
forum: Server Platforms
---

### Post by grcunning on 2010-12-22
I am moving a webserver from a Gutsy to Lucid server. The webserver works fine, but I am having a problem with the users.
I moved the home directories, along with passwd, group, shadow, and gshadow.
The users can login fine, and their home directories are fine.  The problem is when they try to logout, they get

$logout
-sh: logout: not found

any ideas?

---

### Post by Fir3chi3f on 2010-12-22
What if you use 'exit' to try to logout?

---

### Post by grcunning on 2010-12-22
looks like exit works just fine.  I'd really like them to be able to use logout like they are used to.  Users are creatures of habit.  Can I just create an alias, and if I can, how would I do it for all the users at the same time?

---

### Post by matt_symes on 2010-12-22
Hi

You could create an alias for your users.

Maybe you could add it to

/etc/bash.bashrc

Kind regards

---

### Post by sisco311 on 2010-12-22
logout is  a bash builtin. It seems you are logged in in dash (sh).

---

