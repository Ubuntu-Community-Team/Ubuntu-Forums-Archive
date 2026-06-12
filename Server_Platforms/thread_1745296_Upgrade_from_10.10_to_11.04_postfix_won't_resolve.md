---
title: "Upgrade from 10.10 to 11.04 postfix won't resolve"
date: 2011-04-30
forum: Server Platforms
---

### Post by DigiAngel on 2011-04-30
Topic says it.  Postfix was receiving emails just fine on 10.10, did the upgrade, now every host is unkown...even though I can dig -x from the machine and resolve.  Anyone have any thoughts?  Thanks.

James

---

### Post by DigiAngel on 2011-05-03
No answers eh?  Hehe...good thing I upgraded the backup machine and not the production one

---

### Post by kevin.sumner on 2011-05-03
postfix is unhappy due to some changes with libraries.  I have written a patch for the postfix init script.  Follow the bug here for full info:

[https://bugs.launchpad.net/ubuntu/+source/postfix/+bug/764096](https://bugs.launchpad.net/ubuntu/+source/postfix/+bug/764096)

Cheers!

---

### Post by DigiAngel on 2011-05-03
Thanks Kevin..that helps out.

James

---

