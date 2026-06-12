---
title: "Snapshots... UnionFS?"
date: 2010-03-15
forum: Server Platforms
---

### Post by nhenry on 2010-03-15
I am looking for a way to take a "snapshot" of a machine that I can quickly/securely revert back to.

So for example
[LIST=1]
[*]We have a cloud server (EC2, Rackspace, SliceHost, etc) set up how we want it to be set up...
[*]We loan server out to UserA
[*]UserA uses the system however he/she wants (installing software, adding/removing/changing files, etc)
[*]UserA is done with the server and returns it to us
[*]We run a script to "clean" the server (revert it back to how we had it before).  NOTE: We can not start a brand new server each time, we must try to reuse servers
[*]We loan out the server again to UserB (Assured that the system is the same that it was before UserA used it)
[/LIST]

Can this be accomplished with UnionFS on top of a read only FS or is there some other way that would work better?

Any advice would be appreciated.

---

