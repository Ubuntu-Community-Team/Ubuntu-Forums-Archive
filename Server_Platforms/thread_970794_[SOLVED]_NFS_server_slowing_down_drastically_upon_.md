---
title: "[SOLVED] NFS server slowing down drastically upon user logons"
date: 2008-11-04
forum: Server Platforms
---

### Post by wilbbe01 on 2008-11-04
We are running around 40 machines in a lab environment of which all use NFS and one server.  When a few users log in (like even only 10) the load averages on the server jump as high as 5 (yes, gasp, 5).  After machines have been logged in for a while the load averages drop and machines become more usable again.  I know this server is slower than it could be, but at the same time we previously used SuSE and we did not experience slow load times like this.  Does anyone know of any files in Ubuntu which upon user log on read a lot of data?  Anyone have any ideas why things slow down so drastically?  Any ideas of what to look into would be appreciated.  Thanks.

---

### Post by wilbbe01 on 2008-11-30
The answer was found within a professor's computer.  Their machine was using Beagle, and indexing the entire NFS share every hour.  Now it's solved!

---

