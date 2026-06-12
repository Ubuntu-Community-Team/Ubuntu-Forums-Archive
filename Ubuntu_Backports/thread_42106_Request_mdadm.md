---
title: "Request: mdadm"
date: 2005-06-16
forum: Ubuntu Backports
---

### Post by steven_ellis on 2005-06-16
Having some problems startin up my raid arrays correctly that look to be fixed in the Breezy update to mdadm. Any chance of a backport?

Steve

---

### Post by Seth on 2005-06-16
[QUOTE=steven_ellis]Having some problems startin up my raid arrays correctly that look to be fixed in the Breezy update to mdadm. Any chance of a backport?

Steve[/QUOTE]
 Yep.

[http://sethkinast.com/ubuntu/hoary/backports/mdadm_1.11.0-0ubuntu1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/mdadm_1.11.0-0ubuntu1~5.04ubp1_i386.deb)

---

### Post by jdong on 2005-06-16
See if that works for you. I don't want to introduce such a core component into Backports unless it definitely works and definitely fixes a problem.

A bad mdadm package could render some users' configurations to be unbootable.

---

