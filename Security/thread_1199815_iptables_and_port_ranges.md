---
title: "iptables and port ranges"
date: 2009-06-29
forum: Security
---

### Post by jujitsu-nut on 2009-06-29
Hi folks.

I'm wondering if someone would be able to explain default ports in iptables. Sepcifically, let's look at a default INPUT policy set to DROP:

*filter
:INPUT[2:452]

Does the above mean that ports 2:452 are not blocked here or does it mean something else? I have seen other examples like this:

*filter
:INPUT[0:0]

I hate to assume but it seems as though anything above port 0 would be blocked here...

If anyone can help set me straight on this I would appreciate it very much!

--james

---

### Post by jujitsu-nut on 2009-06-29
Never mind... I figured out. Number of packets and aggregate of of traffic in bytes.

---

