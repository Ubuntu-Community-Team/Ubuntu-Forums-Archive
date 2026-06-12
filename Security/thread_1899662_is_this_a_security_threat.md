---
title: "is this a security threat?"
date: 2011-12-24
forum: Security
---

### Post by yashar on 2011-12-24
here is my server firewall log file:

```

Dec 21 19:15:24 [93166.520580] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1943
Dec 21 19:15:26 [93169.058502] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1945
Dec 21 19:15:29 [93172.242290] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1942
Dec 21 19:15:31 [93173.951240] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1944
Dec 21 19:15:43 [93186.170206] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1938
Dec 21 19:15:43 [93186.063278] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1946
Dec 21 19:15:44 [93186.800319] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1949
Dec 21 19:15:45 [93187.901140] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1943
Dec 21 19:15:48 [93190.578242] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1945
Dec 21 19:15:55 [93197.847511] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1942
Dec 21 19:16:20 [93222.980281] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1939
Dec 21 19:16:22 [93225.338069] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1946
Dec 21 19:16:23 [93226.019148] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1938
Dec 21 19:16:23 [93225.960935] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1949
Dec 21 19:16:28 [93230.698764] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1943
Dec 21 19:16:31 [93233.705663] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1945
Dec 21 19:16:46 [93249.128657] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1942
Dec 22 13:50:08 [160050.901213] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1552
Dec 22 13:50:13 [160056.171952] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1540
Dec 22 13:50:14 [160056.500744] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1553
Dec 22 13:50:15 [160058.355601] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1544
Dec 22 13:50:17 [160059.775725] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1545
Dec 22 13:50:17 [160059.519633] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1537
Dec 22 13:50:21 [160063.897185] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1547
Dec 22 13:50:27 [160069.737088] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1559
Dec 22 13:50:34 [160076.771504] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1572
Dec 22 13:50:39 [160081.881102] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1578
Dec 22 13:50:45 [160088.218705] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1540
Dec 22 13:50:50 [160093.119424] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1545
Dec 22 13:50:57 [160099.923979] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1554
Dec 22 13:51:03 [160105.945768] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1562
Dec 22 13:51:08 [160111.030385] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1575
Dec 22 13:51:15 [160118.160990] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1578
Dec 22 13:51:22 [160125.213394] DROP-INPUT eth1 1 tcp packet from 80.239.224.48 (80-239-224-48.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1593
Dec 22 14:28:05 [162328.269700] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1637
Dec 22 14:28:06 [162328.516532] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1632
Dec 22 14:28:07 [162330.086314] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1642
Dec 22 14:28:10 [162333.169165] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1649
Dec 22 14:28:12 [162334.677236] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1645
Dec 22 14:28:15 [162338.340977] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1653
Dec 22 14:28:22 [162345.165522] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1640
Dec 22 14:28:23 [162346.341546] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1679
Dec 22 14:28:29 [162352.338099] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1663
Dec 22 14:28:36 [162358.420600] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1645
Dec 22 14:28:42 [162365.364327] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1682
Dec 22 14:28:48 [162371.279926] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1694
Dec 22 14:29:00 [162382.992457] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1640
Dec 22 14:29:00 [162382.930247] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1685
Dec 22 14:29:07 [162389.376772] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1671
Dec 22 14:29:12 [162394.918359] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1656
Dec 22 14:29:18 [162401.045083] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1677
Dec 22 14:29:24 [162406.418769] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1691
Dec 22 14:29:31 [162413.460431] DROP-INPUT eth1 1 tcp packet from 80.239.224.19 (80-239-224-19.customer.teliacarrier.com) port 443 to 192.168.0.1 (-) port 1695

```
firewall not log more that 10 drop per minute...

is this a port scanning?

what should i do?

---

### Post by jeremywc on 2011-12-24
According to WHOIS, that IP is owned by Akamai, so I doubt it's anything malicious. And anyway, the packets were dropped by the firewall.

[http://whois.domaintools.com/80.239.224.19](http://whois.domaintools.com/80.239.224.19)

---

### Post by Ms. Daisy on 2011-12-24
The wiki in my signature has a section towards the end called "Did I just get owned?" which can help you understand some logs.

---

### Post by Dangertux on 2011-12-24
Nothing from that indicates anything malicious. If you want more in depth info post a packet capture of this traffic.

---

### Post by Lars Noodén on 2011-12-25
> **Ms. Daisy said:**
> The wiki in my signature has a section towards the end called "Did I just get owned?" which can help you understand some logs.

By putting the important link in the body of the comment, it will be there in the archive even after you change your signature to something else later:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by yashar on 2011-12-25
>  If you want more in depth info post a packet capture of this traffic.
it is on port 443 , it would be encrypted, what could i get from encrypted data?

sorry but i dont understand. i see the ip owner is ok, but beside that why it tried to SYN with many ports.

Ms.daisy, the link in your signature not working.

---

### Post by OpSecShellshock on 2011-12-25
If the traffic is what it looks like then the computer at 192.168.0.1 is the client and the other IP addresses are the servers. 443 is the server-side https port so since it is showing up as the source port in these events, what we're most likely looking at is a response from those IP addresses to a request sent out by 192.168.0.1. The connection request is going out to the external IPs, but the response from them is being dropped, which is what I think is generating these events in the log.

---

### Post by Dangertux on 2011-12-25
> **yashar said:**
> it is on port 443 , it would be encrypted, what could i get from encrypted data?

sorry but i dont understand. i see the ip owner is ok, but beside that why it tried to SYN with many ports.

Ms.daisy, the link in your signature not working.


Packet Header, and OpSecShellshock is correct. The reason it is probably trying to SYN/ACK in response to a request client side so many times is it is being dropped for whatever reason.

---

### Post by Lars Noodén on 2011-12-25
> **Dangertux said:**
> Packet Header, and OpSecShellshock is correct. The reason it is probably trying to SYN/ACK in response to a request client side so many times is it is being dropped for whatever reason.

Would that be an additional reason to [use REJECT instead of DROP](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)?  The default iptables policies only allow DROP or ACCEPT so to [use REJECT instead of DROP](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject) it is necessary to append it to the end of the INPUT chain.

---

### Post by Dangertux on 2011-12-25
> **Lars Noodén said:**
> Would that be an additional reason to [use REJECT instead of DROP]("http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/")?  The default iptables policies only allow DROP or ACCEPT so to [use REJECT instead of DROP]("http://www.chiark.greenend.org.uk/%7Epeterb/network/drop-vs-reject") it is necessary to append it to the end of the INPUT chain.

It's not required, but it certainly can cutdown noise in logs if you use REJECT --reject-with tcp-reset , or in some cases icmp-port-unreachable. Though reset should be more than adequate.

hope this helps

---

### Post by yashar on 2011-12-26
understood, thanks

---

### Post by Ms. Daisy on 2011-12-26
> **Lars Noodén]By putting the important link in the body of the comment, it will be  there in the archive even after you change your signature to something  else later:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)[/QUOTE] Thanks Lars :)

[QUOTE=yashar said:**
> Ms.daisy, the link in your signature not working. Did you get it to work? Try cutting & pasting it instead of clicking.

---

