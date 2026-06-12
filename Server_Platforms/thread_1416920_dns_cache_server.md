---
title: "dns cache server"
date: 2010-02-26
forum: Server Platforms
---

### Post by dsexton18 on 2010-02-26
dns cache ser    This is probably more of a network question but I figured some one who is a network expert might know.  Currently my organization has DNS servers.  But my questions is would setting up a cache server improve the performance any?  When I first thought about it i thought probably not.  But since it stores information in ram that made me think maybe it would improve network performance a little.

---

### Post by joberly on 2010-02-26
It will improve network performance. Instead of leaving the network to query the nameservers, they save a step and do it right on the internal network for sites that have been previously visited.

However it's not recommended to use the same server as your internal DNS and your cacheing name server.

---

### Post by Bachstelze on 2010-02-26
> **dsexton18 said:**
> dns cache ser    This is probably more of a network question but I figured some one who is a network expert might know.  Currently my organization has DNS servers.  But my questions is would setting up a cache server improve the performance any?  When I first thought about it i thought probably not.  But since it stores information in ram that made me think maybe it would improve network performance a little.

If your organization has DNS servers already, running your own would make no noticeable improvement. Querying another machine on a network will only take a few milliseconds longer than querying localhost.

---

### Post by dsexton18 on 2010-02-26
That's kind of what I thought.  One more question any one know how to view the contents of cached sites on dnsmasq or am I not able to do that?

---

