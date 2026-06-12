---
title: "ACL (access control lists)"
date: 2008-10-03
forum: Security
---

### Post by sulekha on 2008-10-03
Hi,


why it is said that enabling ACLs(access control lists) can reduce performance  or do not enable ACL on file systems that holds system files, where traditional Linux permissions are sufficient?

---

### Post by bodhi.zazen on 2008-10-03
Well, one could imagine that if you enable ACL it is just one more thing for the system to check and thus there will be a performance hit.

In reality, I do not notice a difference in speed or performance with SELinux active vs inactive (SELinux is basically a system wide ACL). I seriously doubt you will notice any performance difference with any modern hardware after enabling ACL (just my 2c).

What is it that you are reading ? Why do you need ACL ?

---

