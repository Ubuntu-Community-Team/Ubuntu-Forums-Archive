---
title: "Server for network monitoring"
date: 2010-09-08
forum: Server Platforms
---

### Post by redelek on 2010-09-08
Hi,
I want to put a server to monitor users' work.
I have a schedule

INTERNET-> router-> Server Monitoring-> SWITCH

As for the server to enable monitoring of the transmission of all packets from eth0 to eth1?
Is it enough
```
sudo echo "1"> / proc/sys/net/ipv4/ip_foward
```

I will be grateful for the help and information

Best regards
Redelek

---

### Post by spynappels on 2010-09-08
That command will only enable packet forwarding, not monitoring as such. What exactly are you trying to check up on? Wireshark or TCP dump can sniff packets and filter the results...

---

### Post by redelek on 2010-09-09
Yes, I know
Applications to the Cacti monitoring, nagios, snort.
I mean to include the transmission of all packets from eth0 to eth1 without modification or masquerade

---

