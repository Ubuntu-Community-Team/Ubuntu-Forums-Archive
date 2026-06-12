---
title: "Multiple Openvpn Instances"
date: 2012-08-30
forum: Server Platforms
---

### Post by tunbosun on 2012-08-30
Pls I have a VPS running Ubuntu 12.04.
I installed Openvpn on it and want to run two server instances on it.

In the first .conf file 
I specify a different port 9200 and unser the server command i have
server 10.8.0.0 255.255.255.0


In the second .conf file
I specify a different port 500 and unser the server command i have
server 11.8.0.0 255.255.255.0

I issued the following command

iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -s 10.8.0.0/24 -j ACCEPT
iptables -A FORWARD -s 11.8.0.0/24 -j ACCEPT
iptables -A FORWARD -j REJECT
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
iptables -t nat -A POSTROUTING -s 11.8.0.0/24 -o eth0 -j MASQUERADE

I also inserted this command into /etc/rc.local

#!/bin/sh -e
#
# [...]
#

iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -s 10.8.0.0/24 -j ACCEPT
iptables -A FORWARD -s 11.8.0.0/24 -j ACCEPT
iptables -A FORWARD -j REJECT
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
iptables -t nat -A POSTROUTING -s 11.8.0.0/24 -o eth0 -j MASQUERADE

exit 0

On the client I have specified the different port in the .ovpn file

The problem i have is that anytime i connect through port the .ovpn file that has port 9200 i get connected and i can access the internet, but anytime I connect through the .ovpn file that has port 500 it connects successfully as well but I can't access the interent.

What can I do.

Thanks

---

### Post by SeijiSensei on 2012-08-30
1)  First, don't use a port below 1024 like 500 for OpenVPN.  Those are [reserved]("http://tools.ietf.org/html/rfc6335#page-11") for defined services (see /etc/services) and can only be accessed by processes running with root privileges.  If you specify a user/group other than root, like nobody/nogroup, in the configuration for port 500, that could be the problem.  Always choose ports above 1024.  

2)  Similarly, you shouldn't be using the 11/8 network.  There are specifically assigned private IP subnets in [RFC 1918]("http://www.faqs.org/rfcs/rfc1918.html").  Use subnets of 10/8 like 10.1/16 and 10.2/16 instead of 11/8.  (Network 11/8 belongs to the [US Department of Defense]("http://whois.arin.net/rest/net/NET-11-0-0-0-1").)  In general, you can't just arbitrarily choose network addresses and port numbers.  Follow the RFCs.  

3)  What does the routing table look like on the VPN server?  Connect to both VPNs, then run "route -n" and show us the results.

4)  What do you see in /var/log/syslog when you try to reach the Internet from the non-functioning network?

---

