---
title: "fail/load balancer?"
date: 2009-06-30
forum: Server Platforms
---

### Post by pytrisss on 2009-06-30
Hi there,
I am looking for a solution to this exact server setting.

I've got one server which should proxy http requests to two backend clients running on two standalone servers behind it.
On those two backend clients there is a database file syncing from master to slave via simple NFS.
What I need is something like apache mod_proxy_balancer but with the ability to set the master to which it will proxy all the requests by default and when the master goes down it switches to slave.
mod_proxy_balancer unfortunately cant do that :(

Any sugestions?
Thx

---

