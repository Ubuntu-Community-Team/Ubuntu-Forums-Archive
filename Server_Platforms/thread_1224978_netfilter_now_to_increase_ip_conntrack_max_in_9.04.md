---
title: "netfilter: now to increase ip_conntrack_max in 9.04?"
date: 2009-07-28
forum: Server Platforms
---

### Post by alecm3 on 2009-07-28
I need to increase the number of connections that netfilter module can track on a production server.
On 8.04 it was:
echo 524288 > /proc/sys/net/ipv4/netfilter/ip_conntrack_max
On 9.04, the entire /proc/sys/net/ipv4/netfilter directory is missing. Moreover, find / -name ip_conntrack_max returns NOTHING.
How do I increase this?

---

### Post by alecm3 on 2009-07-28
> **alecm3 said:**
> I need to increase the number of connections that netfilter module can track on a production server.
On 8.04 it was:
echo 524288 > /proc/sys/net/ipv4/netfilter/ip_conntrack_max
On 9.04, the entire /proc/sys/net/ipv4/netfilter directory is missing. Moreover, find / -name ip_conntrack_max returns NOTHING.
How do I increase this?

The answer is that in Ubuntu 9.04 server edition nf_conntrack module apparently is not loaded by default. I wonder why...
When I loaded it
# modprobe nf_conntrack 
the file /proc/sys/net/nf_conntrack_max promptly appeared.
I added nf_conntrack  to /etc/modules
Why was it omitted in 9.04 server?

---

