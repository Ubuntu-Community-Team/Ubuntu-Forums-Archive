---
title: "Nagios check_dhcp - what's this &quot;via&quot; suddenly?"
date: 2010-07-29
forum: Server Platforms
---

### Post by Fatman_UK on 2010-07-29
Hi.

```
me@puter:/usr/lib/nagios/plugins$ ./check_dhcp -s 192.168.23.1 -v -i eth0
DHCP socket: 3
Hardware address: 00:19:b9:xx:xx:xx
DHCPDISCOVER to 255.255.255.255 port 67
DHCPDISCOVER XID: 1512089295 (0x5A20A6CF)
DHCDISCOVER ciaddr:  0.0.0.0
DHCDISCOVER yiaddr:  0.0.0.0
DHCDISCOVER siaddr:  0.0.0.0
DHCDISCOVER giaddr:  0.0.0.0
send_dhcp_packet result: 548




recv_result_1: 300
recv_result_2: 300
receive_dhcp_packet() result: 300
receive_dhcp_packet() source: 192.168.23.1
Result=OK
DHCPOFFER from IP address 192.168.23.2 via 192.168.23.1
DHCPOFFER XID: 1512089295 (0x5A20A6CF)
DHCPOFFER chaddr: 0019B9xxxxxx
DHCPOFFER ciaddr: 0.0.0.0
DHCPOFFER yiaddr: 192.168.23.127
DHCPOFFER siaddr: 192.168.23.2
DHCPOFFER giaddr: 0.0.0.0
Option: 53 (0x01)
Option: 1 (0x04)
Option: 58 (0x04)
Option: 59 (0x04)
Lease Time: 0 seconds
Renewal Time: 43200 seconds
Rebinding Time: 75600 seconds
Added offer from server @ 192.168.23.2 of IP address 192.168.23.127


No (more) data received (nfound: 0)
Result=ERROR
Total responses seen on the wire: 1
Valid responses for this machine: 1
CRITICAL: Received 1 DHCPOFFER(s), 0 of 1 requested servers responded, max lease time = 0 sec.
```

This worked yesterday. 192.168.23.1 is the DHCP server. 192.168.23.2 is the Nagios box. Why would it think it's getting DHCP from itself via the DHCP server? *headscratch*

---

