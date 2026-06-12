---
title: "Multiple threads reading from same socket."
date: 2011-03-05
forum: Server Platforms
---

### Post by darshan123 on 2011-03-05
Hi,

Is it fine if i have a single server fd which is read by multiple  threads ?
Like i will have a one-to-many server and the recv is called in multiple  threads (since there is no connect/accept prob with one to many  server). Also will a blocking and non-blocking fd make a difference in  this case?

Actually I have randomly tried this which works ok, but I am extremely  skeptical. If there is some mutex lock inside recv, then i might not  achieve any gain at all.

Darshan.

---

