---
title: "What are people using for DHCP for IPv6"
date: 2009-01-25
forum: Server Platforms
---

### Post by spectre_25gt on 2009-01-25
I've just started getting IPv6 up and running on my network and I need a DHCP server to configure DNS settings and ddns. So far I've found wide-dhcpv6-server, but the documentation is abysmal. Are there any other packages available or any how-tos for setting things up?

---

### Post by wirelessmonkey on 2009-01-26
I've done a little bit of testing with wide-dhcpv6-server against windows dhcp server and wide-dhcpv6-client.

---

### Post by spectre_25gt on 2009-01-26
Have you gotten a chance to do much configuration? What did you use for reference?

---

### Post by netztier on 2009-01-27
> **spectre_25gt said:**
> Are there any other packages available or any how-tos for setting things up?

A while ago (more than a year), I used dibbler-server and dibbler-client with quite limited success; the local IPv6 project then drifted away and I never looked at it again. It might be better now.

regards

Marc

---

### Post by spectre_25gt on 2009-01-27
Thanks. I'll look into that a bit. The website definitely seems to have a good amount of information on it.

---

### Post by spectre_25gt on 2009-01-30
Well, I got dibbler-server up and running at home. I can't seem to find anything on ddns, though. Also, 8.04 ships with dibbler 0.6.1, so I'm thinking I may be upgrading to 8.10 to get myself a bit more up to date.

---

### Post by spectre_25gt on 2009-02-20
Just wanted to give an update. I've decided to abandon DHCPv6 for the time being as OS X does not have a DHCPv6 client and is not likely to get one anytime soon. It relies solely on router discovery. Most of the clients on my network are Macs, so it would be pointless for me to pursue that method.

I haven't really found a good option for service discovery yet. I did, however, find an RFC on the subject. It's available at [http://www.ietf.org/rfc/rfc4339.txt](http://www.ietf.org/rfc/rfc4339.txt)

---

