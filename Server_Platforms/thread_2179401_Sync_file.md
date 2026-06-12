---
title: "Sync file"
date: 2013-10-08
forum: Server Platforms
---

### Post by Bondar_Mircea on 2013-10-08
I have two server apache/php, mysql. What is the best way to sync. the both servers...like raid 1?

---

### Post by SeijiSensei on 2013-10-08
Do you mean you want to make sure one server has the same files as the other?  Use [rsync](http://rsync.samba.org/).

If you mean you want the servers to run in parallel and distribute the same web content, that's a much more complicated question.  If that's what you want to do, we can talk about that as well.

---

