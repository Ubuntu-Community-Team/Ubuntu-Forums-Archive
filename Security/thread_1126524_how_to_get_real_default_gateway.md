---
title: "how to get real default gateway"
date: 2009-04-15
forum: Security
---

### Post by se_landy on 2009-04-15
i have a problem. when I'm connecting to Internet i get connected... but i can't open any web site!!
I turned wireshark on, and I see that there are more devices with ip address 10.1.0.1 (which is ip address for default gateway and default dns server). When i try to connect I always get the wrong DHCP acknowledge. Can I do anything to block the computer that sends me "fake" acknowledgments and to get those from "real" default gateway??? I have MAC address of both of them if it helps...

---

### Post by HermanAB on 2009-04-15
Yes, you can force dhclient to listen only to a specific DHCP server.  Read 'man dhclient' and 'man dhclient.conf'.  You need to create /etc/dhclient.conf and add a line or two to it, that's all.

---

