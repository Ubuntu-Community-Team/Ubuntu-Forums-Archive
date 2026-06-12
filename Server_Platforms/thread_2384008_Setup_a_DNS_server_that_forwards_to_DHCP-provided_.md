---
title: "Setup a DNS server that forwards to DHCP-provided DNS server"
date: 2018-02-01
forum: Server Platforms
---

### Post by rayleighjones on 2018-02-01
Hello,

I'm running in an annoying problem, and I can't find anything about it on the internet.

For testing purposes, I'm currently trying to setup a network between several VM, hosted on a W10 system with Virtual Box. 

I have a router with eth0 connected to the internet through Virtual Box's NAT network, and eth1 connected to an internal virtual LAN.
Let's say I have one or several clients, connected only to the internal virtual LAN.

I've setup the route table on my router, installed and configured isc-dhcp-server on it, set my clients to ask for a dhcp on their eth0, and setup the NAT on my router with iptables.
Everything works, I can ping external IPs (8.8.8.8) from my client, and other clients, so all the IP part is good.

Here's the problem, when I did the first tests, I was home and I had setup my router's eth0 with a static config, using google's DNS, I also had isc-dhcp-server to provide google's DNS to clients.
Then I tried to use that at my school, with their network, and it stopped working. Then I remembered that their network does'nt allow to use a dns they don't provide, which means I have to setup my router so it uses dhcp to get its dns.

But how can I give automatically that DNS to my clients?

I search a way to configure isc-dhcp-server so that it uses automatically the dns provided by the dhcp request on eth0.

Or I can use a bind9 server, but the same question applies: how do I config it so it forwards the requests to a DNS that is provided by a DHCP request?

Thank in advance, and excuse my English if it's weird.

---

