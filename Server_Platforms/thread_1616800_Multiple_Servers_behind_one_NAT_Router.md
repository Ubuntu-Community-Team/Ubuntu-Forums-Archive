---
title: "Multiple Servers behind one NAT Router"
date: 2010-11-08
forum: Server Platforms
---

### Post by polc1410 on 2010-11-08
I've googled hard and got no where useful.  

I have a single public IP Address (80.xx.xx.xx) - its not possible to make that more than one IP address, if it was possible to add more than one IP I'd use the second IP to add network resilience.

I have a single Netgear Router (192.168.1.1) running at that IP which has a DHCP Server on it allocating IPs in the range 192.168.1.100-150 and other machines are allocated static IPs in the 192.168.1.xxx domain.

I have a server which runs Apache2 with virtual hosts (192.1.68.1.50) - its been in use for some years.  However, when I take a development on that site from 'dev' to 'production' its a fair chunk of work.  So I have decided to run all my new developments as virtual boxes.  I can then simply copy the virtual appliance to a new virtual server out in the big world.

So I currently have 4 projects on 192.168.1.200 - 204, they are ready to go out for public testing.  But now I realise I need to do more than just add an IP to a router.

The options I've seen are:

* Host everything in one server and use Apache Virtuals - not a solution as described above I want virtual appliances.
* Use port forwarding... I could have 12 or more virtual servers on the go so would prefer not to go this route
* Use a proxy server.  I don't often use HTTPS but I do occassionally, and it'd be nice to know how to have more than one site?

What I'm looking for is something like

server1.mydomain.com --> goes to public IP, sent to an internal 'router' (probably the server hosting the virtual boxes [192.168.1.200]) --> 192.168.1.201

server2.mydomain.com --> goes to public IP, sent to an internal 'router' (probably the server hosting the virtual boxes [192.168.1.200]) --> 192.168.1.202

etc

So suggestions please :
:popcorn:

---

### Post by HermanAB on 2010-11-09
Hmm, you can probably do that with a combination of Socat and Squid-cache, but you can only support one SSL connection on port 443.

---

