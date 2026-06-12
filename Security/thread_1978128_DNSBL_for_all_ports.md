---
title: "DNSBL for all ports?"
date: 2012-05-11
forum: Security
---

### Post by antar on 2012-05-11
I run a gaming server that's occasionally inundated by spammers who evade IP bans by using open proxies.

I'd like to block them using blacklists such as [dronebl]("http://dronebl.org/") and [abuse.ch]("http://www.abuse.ch/"). I've found directions as to how to use these blacklists for TCP-wrapped services (such as ssh) through hosts.deny, but the server doesn't use tcp wrapper.

Is there any solution using, say, iptables or UFW that I can use to block all connections on a generic port from an IP on one of these DNSBLs?

---

