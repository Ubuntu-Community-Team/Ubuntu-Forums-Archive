---
title: "Folder Synchronization"
date: 2010-03-23
forum: Server Platforms
---

### Post by polypill on 2010-03-23
I was wondering what the recommended way to set up real-time (or near real-time) folder synchronization among 2+ servers. I looked a rsync but that doesn't sound real-time and it looks like its something that you might put in a cron once an hour.

---

### Post by KB1JWQ on 2010-03-23
rsync is unidirectional.

You want either shared storage (NFS) or unison.

---

