---
title: "LXC: no IPv4 in container when UFW firewall is enabled"
date: 2013-01-19
forum: Virtualisation
---

### Post by cryptochrome242 on 2013-01-19
Hi,

I have a strange problem with LXC (default configuration from Ubuntu 12.10 packages). Containers get their IP addresses via DHCP, probably provided through the lxcbridge. As soon as I enable the UFW firewall on the host, the containers stop receiving IPv4 addresses via DHCP and only have IPv6.

Any ideas for me?

Thanks

---

