---
title: "Request package PPP for breezy"
date: 2006-01-28
forum: Requests
---

### Post by moopere on 2006-01-28
I just realised I posted this originally in the wrong area, so heres the formal request:

1) Version requested: PPP 2.4.4b1-1ubuntu1

2) I don't think backporting this package will have a negative effect on the rest of the system.  I did a straight install from the dapper repo's and it only had one dependency requiring upgrade (and probably won't with a backport).

3) Why?  Because of this serious bug in the version available in Breezy:

[https://launchpad.net/distros/ubuntu/+source/rp-pppoe/+bug/28652]("https://launchpad.net/distros/ubuntu/+source/rp-pppoe/+bug/28652")

Which did not effect hoary of warty users.  

The bug does not allow a user setable MTU size, which will almost certainly effect DSL modem users, particularly badly off will be those (like me) who run a NAT box and have several machines behind it trying to access the internet as the packet sizes will be too large and will fail to route correctly.

Cheers,
Craig

---

