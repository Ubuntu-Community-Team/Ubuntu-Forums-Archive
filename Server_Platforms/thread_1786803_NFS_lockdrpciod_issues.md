---
title: "NFS lockd/rpciod issues"
date: 2011-06-20
forum: Server Platforms
---

### Post by niax on 2011-06-20
We run quite a few clients of various distributions off a single NFS (both v3 and v4) server running Ubuntu Server 10.04.2 64bit

A couple of the clients (those who have their home directories on the file server that run debian or ubuntu) will randomly lock up from time to time. From the [kern.log]("http://pastebin.com/bg3rcu5V") lockd is complaining about not being able to talk to the clients also some issues with statd.

Looking closer, it also seems that rpciod is going into a deadlocked state, which is worrying.

Rebooting the server fixes the issue for a couple of hours, but rebooting the server every few hours isn't a fix.


Thanks in advance,
Nick

---

