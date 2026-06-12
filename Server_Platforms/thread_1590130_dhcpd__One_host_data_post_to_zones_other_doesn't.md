---
title: "dhcpd:  One host data post to zones other doesn't"
date: 2010-10-07
forum: Server Platforms
---

### Post by Jsdey on 2010-10-07
host declarations identical for robo2 and robo3 in dhcpd.conf.  robo6 is running ubuntu; robo2 is on an old Power Mac G5 running os x 10.3.9.  robo6 updates zones; robo2 doesn't.  The relevant syslog output is shown below.  Is there anyway I can force robo2 to update zones?  Thanks.

```
syslog:

robo2
Oct  7 10:52:40 robo5 dhcpd: uid lease 192.168.0.103 for client 00:0a:95:a7:c8:26 is duplicate on 192.168.0/24
Oct  7 10:52:40 robo5 dhcpd: DHCPREQUEST for 192.168.0.2 from 00:0a:95:a7:c8:26 via eth0
Oct  7 10:52:40 robo5 dhcpd: DHCPACK on 192.168.0.2 to 00:0a:95:a7:c8:26 via eth0

robo6
Oct  7 10:54:56 robo5 dhcpd: DHCPDISCOVER from 00:1e:37:24:0d:a2 via eth0
Oct  7 10:54:56 robo5 dhcpd: DHCPOFFER on 192.168.0.6 to 00:1e:37:24:0d:a2 via eth0
Oct  7 10:54:56 robo5 dhcpd: Added new forward map from robo6.robo.net to 192.168.0.6
Oct  7 10:54:56 robo5 dhcpd: added reverse map from 6.0.168.192.in-addr.arpa. to robo6.robo.net
Oct  7 10:54:56 robo5 dhcpd: DHCPREQUEST for 192.168.0.6 (67.63.55.3) from 00:1e:37:24:0d:a2 via eth0
Oct  7 10:54:56 robo5 dhcpd: DHCPACK on 192.168.0.6 to 00:1e:37:24:0d:a2 via eth0

```

---

