---
title: "Fail2Ban + custom iptable rules = mess."
date: 2011-11-03
forum: Security
---

### Post by sandyd on 2011-11-03
I currently have my own set of iptable rules to prevent access to some of my servers that are proxied by nginx. The problem is, I also run fail2ban on my mailserver. Each time fail2ban bans a server, it vanishes ALL my iptable rules, and adds its own.

When I restart iptables, my normal set of rules appear.

WTH?

---

### Post by Dangertux on 2011-11-04
fail2ban should update a custom iptables chain so it shouldn't be doing this.

Make sure that your configuration file specifies that fail2ban is creating and appending these rules to a custom chain, and that it isn't running anything that flushes the normal iptables other than it's custom chain.

Hopefully this works for you.

Alternatively you may consider using iptables to rate limit connections to your mail server.

---

