---
title: "Network Inventory utility recommendation wanted"
date: 2009-10-23
forum: Security
---

### Post by keevill on 2009-10-23
I am seeking recommendations for a network scanner - basically to give me such info as which IP addresses are live on the current time and perhaps traffic information although that's not so important.

---

### Post by __p1n__ on 2009-10-23
You don't need a scanner to see which hosts (virtual or otherwise) are up.  Just use the ping command which was designed exactly for this purpose

Other approaches include scanning/initiating ARP traffic; netdiscover is an extremely specialized tool that does exactly that.

You can use nmap to perform both ICMP and ARP based host status checks however it's total overkill and you can do both those things using either ping or netdiscover.

If you run wireshark on your interface (instead of a packet capture file) you can discover which hosts are up however you will have to wait for traffic to/from/about each host.  This approach also lets you see all the traffic (if your nic is in promiscuous mode and you're not on a switched network or are on a switched network but are running ettercap to defeat that.)

You really just need ping though.

---

### Post by QLee on 2009-10-23
> **keevill said:**
> I am seeking recommendations for a network scanner - basically to give me such info as which IP addresses are live on the current time and perhaps traffic information although that's not so important.

My router, which also hands out the IP addresses has a page with just such information. Probably yours does too. ...Or are you looking for something that will give you information on a system where you are not the admin?

---

### Post by The Cog on 2009-10-23
Have a look at nmap - that kind of thing is what it was written for.

---

### Post by cariboo on 2009-10-23
I use the following nmap command to check the ip addresses of the computers that get their ip address via dhcp.

```
sudo nmap -PR -sP 192.168.1.0/24
```

Most of the computers on my network have static ip addresses, but there are 4 that use dhcp, so the command comes in handy at times.

---

