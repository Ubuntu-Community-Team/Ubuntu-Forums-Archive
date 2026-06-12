---
title: "DHCP failover peer not returning free leases to primary when down"
date: 2010-10-26
forum: Server Platforms
---

### Post by Instantkarma! on 2010-10-26
Hi,

We have a network with 2 DHCP servers that act as a failover/load balancing pair, which seemed to be working OK.

Today, the power supply of one of the servers (the secondary) failed and the server went down causing the primary to handle all DHCP requests. The primary seemed to be doing fine until this came up in the logs:
```
dhcpd: DHCPDISCOVER from (MAC-adress) via eth0: peer holds all free leases
```The server stopped leasing new IP's apperently because the secondary DHCP server didn't return his half of the reserved address leases when it went down. 

AFAIK, the primary should have taken over the other half of the reserved leases when the secondary went down but somehow it didn't.

The failover section in dhpd.conf contains the following:
```
failover peer "dhcp" {
       primary;
       address [IP-ADRESS 1];
       port 519;
       peer address [IP-ADRESS 2];
       peer port 520;
       max-response-delay 30;
       max-unacked-updates 10;
       mclt 3600;
       split 128;
       load balance max seconds 3;
}

```Any idea what could be wrong here?
Thanks.

---

