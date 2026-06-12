---
title: "Very slow subdomains on local computers"
date: 2007-06-16
forum: Server Platforms
---

### Post by strixy on 2007-06-16
I have a server running and working well for anyone outside of the LAN. For users on the LAN all the TLD's hosted on that server work great, but accessing anything with a subdomain takes forever to load.

eg. myhosteddomain.tld is zippy fast but user.myhosteddomain.tld is really, painfully, slow.

Anyone have any suggestions? What kind of information do you need? I'm not even sure where to start.

Server is running Feisty 7.04. Two computers on the LAN are also running Feisty. DNS is handled by the router. All computers have static internal IP's. DHCP is off.

---

### Post by nixfaced on 2007-06-17
A bit of a shot in the dark, but check reverse DNS.  Forward DNS may work fine (i.e. finding the IP address for a given hostname) but reverse DNS, which is used by many server apps for access control and logging purposes, may not be handled by your router.  

To check this, do something like "host xx.yy.zz", substituting a valid, in-use IP address on your LAN.  If there is no reverse DNS mapping, there is a reasonable chance that your access is being slowed down by failed RDNS lookups.  Alternately, fire up a packet sniffer (tcpdump or wireshark, for example) on the server during testing to see if your server's doing any DNS lookups during the access lag.

Unfortunately, I can't tell you how to fix this, because it would depend on the specifics of your router, but it's a place to start.

Hope this helps.

---

### Post by Mr. C. on 2007-06-18
Your problem is likely due to using your WAN IP vs. LAN IP combined with a poor DNS implementation in your router and its attempt to do NAT loopback.

You should be using LAN IP addresses on your LAN, not WAN IP addresses.  This requires that you either enter valid entries in /etc/hosts, or use your own internal DNS server which you configure as authoritative for your zones.

It is possible that changing your DNS server to those of your ISPs (instead of your router) will workaround the problem.

MrC

---

