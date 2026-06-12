---
title: "drop igmp packets"
date: 2011-01-03
forum: Security
---

### Post by yashar on 2011-01-03
how can i drop igmp port 0 packets with iptables rule?
my log file is full of this router advertisement.

---

### Post by The Cog on 2011-01-03
Logging dropped packets will keep you awake at night worrying about things. I advise that you simply be happy that the packets were dropped. Iptables is doing its job.

That said, igmp is ip protocol number 2. Try:
iptables -A INPUT -p 2 -j DROP
or
iptables -A INPUT -p igmp -j DROP

Be aware that doing this may prevent any multicast applications you run from working properly.

---

### Post by bodhi.zazen on 2011-01-03
> **yashar said:**
> how can i drop igmp port 0 packets with iptables rule?
my log file is full of this router advertisement.

Post the logs.

Otherwise, do not log such trivial traffic.

You really should not be using your logs to monitor your network, you need to use a tools such as snort to filter all the packets for "alerts" or concerning traffic, then turn off logging in iptables.

---

