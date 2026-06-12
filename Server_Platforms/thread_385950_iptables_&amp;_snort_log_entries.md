---
title: "iptables &amp; snort log entries"
date: 2007-03-16
forum: Server Platforms
---

### Post by jtapper on 2007-03-16
I have been using iptables and snort in my server for a while. Now when I check snort logs I find entries from ip-addresses / net work blocks filetered by iptables.
Does snort process packets before iptables or how is this possible?

Situation is that I have few hundred rules in iptables for certain abusive IP blocks. And even these appear in
```
 iptables -L -n -v
```
with DROP marking, some of these still make it to snort alert logs. Iptables seem to work, because the counters for rules are working.

Can anyone confirm that snort sniffs packets before they are iptables processed or is my iptables malfunctioning?

---

### Post by wray.justin on 2007-03-19
jtapper:

     Is 'snort' running with INLINE mode?

[URL="http://www.snort.org/docs/faq.html#4.3"]
4.3 --faq-- --snort-- --faq-- --snort-- --faq-- --snort-- --faq--

Q: Snort is behind a firewall (ipf/pf/ipchains/ipfilter) and awfully quiet... A: Your firewall rules will also block traffic to the snort processes.[/URL]

However if you are not running in INLINE mode, then snort should see all traffic, even the dropped packets.

---

### Post by jtapper on 2007-03-20
Inline mode is not on, so it seems that this is pretty normal. Thanks!

---

### Post by wray.justin on 2007-03-22
No problem

---

