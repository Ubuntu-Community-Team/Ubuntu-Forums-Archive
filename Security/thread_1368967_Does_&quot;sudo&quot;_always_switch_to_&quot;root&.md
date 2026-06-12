---
title: "Does &quot;sudo&quot; always switch to &quot;root&quot;? What if more root accounts?"
date: 2009-12-31
forum: Security
---

### Post by pstein on 2009-12-31
As well known "sudo" always performs a command automatically with root priviledges?
 
Is there always automatically the "root" user account taken?
 
What if there is a second user account root2 with root priviledges and I want to
perform the command under this account?
 
E.g. to set a different ownership of created files.
 
How can I tell sudo to take root2 as user?
 
Peter

---

### Post by BkkBonanza on 2009-12-31
sudo -u user command
see "man sudo" for all options.

However, I'm not sure you can track a second root account uniquely since it would also have uid=0. You probably need to create a normal user and then add sudo privileges for that user with visudo. That user, having a different uid, would be traceable when sudo is used.

---

