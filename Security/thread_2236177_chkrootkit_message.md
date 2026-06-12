---
title: "chkrootkit message"
date: 2014-07-25
forum: Security
---

### Post by dunbrokin on 2014-07-25
Can somebody explain this to me please?

~$ sudo /usr/sbin/chkrootkit -e
[sudo] password for xx: 
/usr/sbin/chkrootkit: 2709: shift: can't shift that many

---

### Post by bashiergui on 2014-07-25
It's a meaningless message given when you use the -e switch without an arguement.
[https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/597623](https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/597623)


-e is used to whitelist. What are you trying to do?

---

### Post by dunbrokin on 2014-07-25
Thank  you for that, as the bug says the documentation is misleading....I was trying to exclude false positives.

---

### Post by dunbrokin on 2014-07-25
Hmm! it still has the suckit rootkit bug also!

---

