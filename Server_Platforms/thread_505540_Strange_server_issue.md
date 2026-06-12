---
title: "Strange server issue"
date: 2007-07-20
forum: Server Platforms
---

### Post by grapesmoker on 2007-07-20
I'm having a very odd problem with my Ubuntu server. I used to run it from home on a dynamic IP that was linked to a DynDNS domain name. Then an IP address freed up in my lab, so I moved the server there so it would have a static address. I configured the routing table and everything seemed to be working fine; I could access the server from anywhere. Fast forward two days, and the server is not responding. I come in and the computer is still running, but the Ethernet light on the back, where the cable plugs into the NIC, is out. So, I did the first thing that occurred to me, which was to unplug the cable and plug it back in. When I did that, I could access everything again! However, after some indeterminate period of time, I experienced the exact same problem. Each time, unplugging the cable and plugging it back in fixes things, but I have no idea why. Has anyone ever had this issue? What could possibly be causing this behavior? Thanks in advance for any help you can offer me.

---

### Post by Mr. C. on 2007-07-20
Look at the messages in /var/log/syslog or dmesg to see any log entries when the NIC goes down.

MrC

---

