---
title: "hardening sys.ctl - one question"
date: 2008-12-13
forum: Security
---

### Post by Gen2ly on 2008-12-13
I've been looking to add a little bit of security to my laptop and I'm using an example that looks repetative:

```
# Disables IP source routing
net.ipv4.conf.all.accept_source_route = 0
net.ipv4.conf.lo.accept_source_route = 0
net.ipv4.conf.eth0.accept_source_route = 0
net.ipv4.conf.default.accept_source_route = 0

# Enable IP spoofing protection, turn on source route verification
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.lo.rp_filter = 1
net.ipv4.conf.eth0.rp_filter = 1
net.ipv4.conf.default.rp_filter = 1

# Disable ICMP Redirect Acceptance
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.lo.accept_redirects = 0
net.ipv4.conf.eth0.accept_redirects = 0
net.ipv4.conf.default.accept_redirects = 0
```

Are these values repetative or do I need them all?

---

### Post by Kinstonian on 2008-12-13
IP source routing is an IP option where the source can determine the routers the traffic will take to get to its destination.  I think it's pretty much irrelevant now since it's so common for routers to drop IP source routed packets.

The "Enable IP spoofing protection, turn on source route verification" is I believe *reverse path filtering*, which can be explained [here](http://en.wikipedia.org/wiki/Reverse_path_forwarding)

The "Disable ICMP Redirect Acceptance" should probably be enabled to prevent someone from using ICMP redirect packets to tell your computer to send its traffic to a different router.

---

### Post by Gen2ly on 2008-12-14
good to know more about what the values mean.  i just wondering if are all these values necessary though?  I've seen a couple of examples where just "all" was used.

---

