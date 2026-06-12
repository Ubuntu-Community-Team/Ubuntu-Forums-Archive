---
title: "IP Forwarding"
date: 2014-04-07
forum: Virtualisation
---

### Post by mecheri on 2014-04-07
Hi everyone,


I have installed kvm on my ubuntu pc.
I have created 3 VMs, two on the **192.168.122.0 **network and one on the **192.168.100.0** network (see attachment).


When a packet comes from **192.168.100.190 (outside.example.org)** and goes to the **192.168.122.0/24** network. 
The 2 VMs (server.example.com and client.example.com) see it as coming from **192.168.122.1** and NOT from **192.168.100.190** as expected !!


_Examples:_


- When I run a ping command from **192.168.100.190 (outside.example.org)** the output of the tcpdump command on **192.168.100.103** shows this:


*# tcpdump -i eth0 -v icmp*
*tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes*
*14:40:57.249450 IP (tos 0x0, ttl 63, id 0, offset 0, flags [DF], proto ICMP (1), length 84)*
***[COLOR=#ff0000]192.168.122.1 > server.example.com[/COLOR]**: ICMP echo request, id 13, seq 1, length 64*


- When I send an http client request (elinks browser) from 192.168.100.190 to the httpd server on 192.168.100.103 the logs file on this shows :


*[COLOR=#ff0000]**192.168.122.1**[/COLOR] - - [06/Apr/2014:14:39:43 +0200] "GET / HTTP/1.1" 200 17*


Any idea ?

---

### Post by SeijiSensei on 2014-04-07
If you are using port forwarding or network address translation, that is the expected behavior.  The incoming packet's source address is rewritten so it appears to come from the router's LAN-facing interface.  The host computer might also be using NAT to support the guest VMs depending on how you configured things.

If you remove any masquerading or similar rules and just let packets route normally without rewriting, you should see the correct addresses.

Having all this working correctly on a bunch of VMs could be very tricky to implement though.

---

