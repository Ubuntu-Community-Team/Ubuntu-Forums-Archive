---
title: "Moblock constantly blocking connections"
date: 2008-05-16
forum: Security
---

### Post by Joe Bedan on 2008-05-16
I am running Moblock with the Mobloquer front-end and it is continuously blocking both incoming and outgoing connections even though I don't even have any P2P software running.

I don't know why the block list only has 6 characters of the name that it is blocking, but it is blocking connections to Consig, Bogon, and [www.wa](www.wa) and a couple of others.

Anyone know why that might be?  Also is there any way to know the full name?

---

### Post by jre on 2008-05-16
Make sure to choose as Blocklist format "peerguardian .p2p text format"
and to have lists like level1.gz in "Blocklists". There must not be an "nipfilter.dat" because this list is in the wrong format.
So, this should fix the 6-letters-problem"

Now you should whitelist your complete LAN, or at least your router's IP.

---

