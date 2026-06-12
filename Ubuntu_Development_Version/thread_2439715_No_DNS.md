---
title: "No DNS"
date: 2020-03-31
forum: Ubuntu Development Version
---

### Post by Doug S on 2020-03-31
Hi All,

I have had 20.04 on my main test computer for a few months now.
I just put the computer on its own static IP address, and in doing so I changed the network interface it is using.

Note 1: Even though I have static external IP addresses, my ISP requires that I obtain them via DHCP lease.
Note 2: This computer is currently using updown and not netplan.

I have no DNS at all, but otherwise the network is working fine.

What I have done so far:
[LIST]
monitored with tcpdump: No DNS requests are being sent upstream, ever.
ping 8.8.8.8 directly: Works fine.
looked at the lease file: Seems O.K., DNS: "option domain-name-servers 198.80.55.5,199.185.220.254;"
looked at resolv.conf: Seems O.K.: "nameserver 127.0.0.53"
Checked that dnsmasq is running.
"resolvectl status" has this line: "Current DNS Server: 198.80.55.5"
route looks O.K.
[/LIST]
DNS was working fine before this change.

Any ideas?

---

