---
title: "SSH session ends prematurely"
date: 2006-02-14
forum: Server Platforms
---

### Post by gte258v on 2006-02-14
I've got SSH running on my server.  When I have two ssh terminals open, and I exit from one of them, the other stops responding.  This also happens with an ssh session and an scp transfer.  As soon as the scp transfer finishes, the terminal session stops responding as well.  The two sessions do not have to be with the same username.  If I open one terminal with user joe, and another with user fred, exiting from one will kill the other.

Anybody have any ideas on why this is happening?

---

### Post by gte258v on 2006-02-20
I found the problem.  The router between the server and the internet was dropping connections for some reason.  I still haven't found anything in the device's manual that mentions this "feature."

---

