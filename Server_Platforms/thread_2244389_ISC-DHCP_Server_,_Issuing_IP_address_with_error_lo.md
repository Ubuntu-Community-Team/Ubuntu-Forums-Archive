---
title: "ISC-DHCP Server , Issuing IP address with error log"
date: 2014-09-16
forum: Server Platforms
---

### Post by Rajitha_wickramasi on 2014-09-16
Hi ,

I have configured DHCPd.conf file to issue IPs to multiple subnets and its working and issuing IPs but it Shows the following error massage in syslog ....I couldn't figure out whats wrong with it .

dhcpd.conf
```

subnet 119.235.101.0 netmask 255.255.255.0 {
  range 119.235.101.2 119.235.101.254;
  option domain-name-servers 202.62.124.238, 202.62.120.4;
  option subnet-mask 255.255.255.0;
  option broadcast-address 119.235.101.255;
  option routers 119.235.101.1;
}
```


Error Message
```

dhcpd: DHCPDISCOVER from 00:0c:e7:a0:be:c8 via 119.235.101.1: unknown network segment
dhcpd: DHCPDISCOVER from 00:0c:e7:a0:be:c8 via 119.235.101.1
dhcpd: DHCPOFFER on 119.235.101.120 to 00:0c:e7:a0:be:c8 (android-62d670aa5e81b098) via 119.235.101.1
dhcpd: DHCPOFFER from 00:0c:e7:a0:be:c8 via 119.235.101.1: unknown network segment
dhcpd: DHCPREQUEST for 119.235.101.120 (202.62.120.8) from 00:0c:e7:a0:be:c8 via 119.235.101.1: ignored (unknown subnet).
dhcpd: DHCPREQUEST for 119.235.101.120 (202.62.120.8) from 00:0c:e7:a0:be:c8 (android-62d670aa5e81b098) via 119.235.101.1
dhcpd: DHCPACK on 119.235.101.120 to 00:0c:e7:a0:be:c8 (android-62d670aa5e81b098) via 119.235.101.1
dhcpd: DHCPACK from 00:0c:e7:a0:be:c8 via 119.235.101.1: unknown network segment

```
From DHCP Server IP have connectivity to 119.235.101.1 ( Default Gateway ) but server says its unknown network Segment ? Why ?
Can someone Pls advice me 


Thanks 

Rajitha

---

### Post by Doug S on 2014-09-16
Hi and welcome to Ubuntu forums,

I'm not really sure what the problem is for your case. I suggest to try this:```
option domain-name-servers 202.62.124.238, 202.62.120.4;
option subnet-mask 255.255.255.0;
option broadcast-address 119.235.101.255;
option routers 119.235.101.1;
subnet 119.235.101.0 netmask 255.255.255.0 {
  range 119.235.101.2 119.235.101.254;
}
authoritative;
```

---

