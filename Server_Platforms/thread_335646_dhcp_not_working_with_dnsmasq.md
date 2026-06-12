---
title: "dhcp not working with dnsmasq"
date: 2007-01-10
forum: Server Platforms
---

### Post by butterman on 2007-01-10
My network looks like this:

atlas --> linksys router <--redfeather

The linksys router is connected to a cable modem.  I want to use dnsmasq for dhcp and dns on atlas. My ISP requires that I run dhcp, so I want to assign a fixed internal IP address to atlas using dhcp.  According to syslog, dnsmasq starts without any errors.  When I try to get an IP address using dhclient eth0, the request goes unanswered.

```
dhclient: No DHCPOFFERS received.
```

I disabled dhcp on the linksys router and confirmed dnsmasq is running.

Here's my dnsmasq.conf:

```
domain-needed
bogus-priv
listen-address=127.0.0.1
expand-hosts
domain=mydomain.net
dhcp-range=192.168.1.200, 192.168.1.219,500h
dhcp-host=00:50:BF:1B:E4:E1,atlas,192.168.1.101,infinite

```

Here's /etc/hosts:

127.0.0.1 localhost atlas
127.0.1.1 atlas
192.168.1.101 atlas

---

