---
title: "Make apport post to multiple package affected bugs"
date: 2012-12-02
forum: The Cafe
---

### Post by Kangarooo on 2012-12-02
Make apport add info to bugs that has many packages specifying package
See bug [https://bugs.launchpad.net/ubuntu/+source/apport/+bug/607478](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/607478)
I tryd adding info using apport-collect 607474 -p xfce4-mixer to bug [https://bugs.launchpad.net/ubuntu/+source/xfce4-volumed/+bug/607474](https://bugs.launchpad.net/ubuntu/+source/xfce4-volumed/+bug/607474) but didnt worked.

Make possible that apport collects info to package if it exists as affected or ask witch package of affected to you want to post info about.

---

### Post by Cheesehead on 2012-12-02
Looking at the bug you posted, it seems to be in the correct place to me.

Some bugs do require multiple packages to be subscribed, but most do not. How to prevent abuse like frustrated or new reporters subscribing a dozen unrelated packages at once?

---

