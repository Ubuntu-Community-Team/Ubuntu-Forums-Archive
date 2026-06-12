---
title: "need help getting squid transparent ip tables right"
date: 2008-05-20
forum: Server Platforms
---

### Post by opportunity on 2008-05-20
Hi guys,

I need help getting squid to be a true transparent proxy. Like many, when i set the web browser proxy to the squid box it works fine but not as a transparent configureless proxy. I heard it was possible to do this with only one NIC and not being directly connected to the WAN connection [packet hijacking] Correct me if im wrong? Right now i only have the squid box connected to the master unmanaged switch. Im thinking i should just use urlfilter with the current ipcop firewall we have rather than create an additional point of failure with squid.




See if there is anything i am missing if it is possible.

So far i have:

Enabled ip forwarding:
echo "1" > /proc/sys/net/ipv4/ip_forward

set the iptables as:
iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp -&#8211;dport 80 -j REDIRECT --to-ports 3128

set the squid.conf as:
http_port 3128 transparent
always_direct allow all

---

### Post by opportunity on 2008-05-20
yeah revamping an existing firewall with the urlfilter is definately the way to fly on this one. Your basically creating a firewall/proxy when you start a squid config. the Ipcop add-on uses powerful squidgaurd for full logging / filtering blacklist / monitoring / etc and its got transparent configureless functionality.

---

