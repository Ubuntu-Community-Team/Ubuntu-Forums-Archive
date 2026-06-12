---
title: "performance issues VMware server 2.0.1 and Ubuntu 9.10"
date: 2009-12-09
forum: Server Platforms
---

### Post by Krijk on 2009-12-09
Yesterday I installed 9.10 (2.6.31-16) with VMware server 2.0.1-156745.
Previously I ran 9.04 with VMware server 2.0.0-122956.

I migrated existing vmware guests and noticed quite a performance difference. The new combination makes python-jobs run considerably slower. Initially they took 5-6 times as long. After some VMware tuning (a.o. [http://www.fewt.com/2008/06/performance-tuning-vmware-server-on.html]("http://www.fewt.com/2008/06/performance-tuning-vmware-server-on.html") ) they still are 3-4 times slower than in the old situation.

I suspect that it has anything to do with the networking part since the vmware uses NFS and an external database. Initially I had some problems installing server 2.0.0  and switched to 2.0.1 with a 2.6.31-14 kernel from [http://radu.cotescu.com/?p=948]("http://radu.cotescu.com/?p=948"). 

Does anybody have any suggestions how to troubleshoot this?

---

