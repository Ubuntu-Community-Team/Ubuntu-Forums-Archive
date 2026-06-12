---
title: "Syncing 2 folders on seperate servers"
date: 2011-08-03
forum: Server Platforms
---

### Post by bigmonmulgrew on 2011-08-03
Hi guys.
I want to be able to sync a folder from one server to another to create a backup in the following format.

ServerA/myfolder  --->  serverB/mybackup/<date>/myfolder

I'm guessing there are lots of ways to automate this process.
Whats the easiest way to do it.

Both servers are currently ubuntu server 11.04

---

### Post by Lars Noodén on 2011-08-03
Look at rsync (over ssh) for the transfer.

---

### Post by bigmonmulgrew on 2011-08-05
Thanks a lot. I've looked over the docs for rsync and it looks exactly what I'm looking for. I'm runnign a test backtp now

---

