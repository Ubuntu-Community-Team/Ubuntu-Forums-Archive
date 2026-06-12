---
title: "high load on idle 10.04.2 system"
date: 2011-04-29
forum: Server Platforms
---

### Post by arjun.shankar on 2011-04-29
I have a rather old laptop (Acer Travelmate 4000 NLCi) running a minimal server install of up to date 10.04.2 with openvpn and some iptables rules. The CPU is happy to run at 600MHz since it is mostly idle.

But it shows a load of 1.0 even while almost completely idle, and goes up if I run anything else (e.g. even just ssh-ing into it, the MOTD complains "load higher than 1").

vmstat says: [http://paste.ubuntu.com/600967/](http://paste.ubuntu.com/600967/)

How do I go about fixing this?

---

