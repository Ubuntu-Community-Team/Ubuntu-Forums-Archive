---
title: "Gateway not forwarding requests?"
date: 2010-03-07
forum: Server Platforms
---

### Post by Jekshadow on 2010-03-07
I have setup a server as the gateway/dhcp server/firewall for my network and everything is working except I cannot access the internet. This is not a DNS issue, when I try to go directly to an IP (I have been using one of Google's IPs, 74.125.19.99) I still cannot access the internet. The server itself can access the Internet, so it must be a routing problem. I have already enabled IPv4 and IPv6 forwarding in /etc/sysctl.conf

```

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
net.ipv6.conf.all.forwarding=1

```

The DHCP server seems to be working fine with this config, clients receive an IP and can connect to other clients on the local network:
```

ddns-update-style none;

option domain-name "loc";
option domain-name-servers 8.8.8.8, 8.8.4.4;

default-lease-time 600;
max-lease-time 7200;

authoritative;

log-facility local7;

subnet 10.0.0.0 netmask 255.255.255.0 {
  range 10.0.0.50 10.0.0.250;
  option routers 10.0.0.1;
  option broadcast-address 10.0.0.255;
  option domain-name-servers 8.8.8.8, 8.8.4.4;
}


```

10.0.0.1 is the server, and 10.0.0.2 is a WiFi router.

---

### Post by adam814 on 2010-03-07
Could you post the output of "sudo iptables -L"?  I'm guessing there's something wrong with the rule to do the actual routing.

---

