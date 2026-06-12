---
title: "SVN through Apache WebDAV"
date: 2008-09-29
forum: Security
---

### Post by jesushero on 2008-09-29
I have an SVN server, running through Apache WebDAV. It is set up to allow anyone to checkout or export anything, but requires a validated user to commit any changes. 

All seems fine, apart from one small (but important) detail! As soon as I commit any changes from a computer and input my password, any subsequent commits from the same computer do not require a password, since it is assumed that the user remains "validated" on the machine! 

Is there any way around this? Is there a way to ask for a password at EVERY commit? Or at least have a timeout? Or a "log-out" function? Or any way to stop allowing commits from a certain machine until the user is re-validated?

---

