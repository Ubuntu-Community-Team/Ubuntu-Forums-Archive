---
title: "Link Aggregation and VMWare Server?"
date: 2009-06-30
forum: Virtualisation
---

### Post by batfastad on 2009-06-30
Hi guys

I've not messed around too much with VMWare and Ubuntu yet (getting a test box going later this week) but I had a general question about whether this was possible.

I'm looking to connect both NICs on my server to our gigabit switch (Netgear GS724T) but using 802.3ad link aggregation they appear as 1 NIC.
I was reading through this how-to [https://wiki.ubuntu.com/LinkAggregation](https://wiki.ubuntu.com/LinkAggregation) and it seems fairly straight-forward in a regular server environment.

But is it possible to do this in a virtualised environment with Ubuntu?

The reason I'm looking to do this is so that users connected to our file server with gigabit cards don't swamp a single link to the server. This should give us increased bandwidth with the advantage of some redundancy.

However I've not even looked into running Ubuntu Server (or JeOS) within VMWare yet but I will be testing that in the next few days.
Just wanted to know if this would be possible. We're consolidating 3 servers into 2 virtual servers to reduce hardware costs and maximise the usage of the server resources.

Cheers, B

---

