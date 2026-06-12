---
title: "gaim-otr 3.0"
date: 2006-01-20
forum: Requests
---

### Post by dguido on 2006-01-20
I'm requesting that gaim-otr 3.0.0 be included in backports due to cryptographic weaknesses found in the previous 2.0 branch.  3.0.0 is in dapper already.  gaim-otr does not depend on anything but its own library, libotr, which would also need to be updated.  I think this is a common sense, easy to handle upgrade and should be done immediately.

The only thing to be careful of is that there are two codebases for the 3.0.0 plugin, one for gaim 1.5 and the other for gaim 2.0.  Both 5.10 and 6.04 use gaim 1.5 at the moment, so it's clear which gaim-otr should be included in the backports.

Links:
[http://www.cypherpunks.ca/otr/](http://www.cypherpunks.ca/otr/)
[http://packages.ubuntu.com/dapper/net/gaim-otr](http://packages.ubuntu.com/dapper/net/gaim-otr)

---

