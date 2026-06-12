---
title: "Heap Space Error"
date: 2011-04-17
forum: Ubuntu Cloud and Juju
---

### Post by Ohm's Lawyer on 2011-04-17
I'm having issues with my Storage Controller. When it first boots up, I can describe my volumes, attach them to instances and everything is fine. However, after a while, I can no longer describe the volumes nor can I attach/detach them. They still work fine within the instances, I can copy to and from them, they are still visible,just not outside.

The error I am getting is a Java Heap Space Error. In my eucalyptus.conf on my storage controller I am showing xmx512 and xms512. That should be enough, but when I try to double it, everything crashes and stops working.

Has anyone else experienced this problem? Any ideas how to fix it?

---

