---
title: "Weird alerts in firestarter"
date: 2009-01-28
forum: Security
---

### Post by fluffybacon on 2009-01-28
Hi Guys,

(this probably isn't security related, but) I was wondering if anyone could explain why I keep seeing this in my firestarter logs: 

> 
In:eth0 Out: Port:995 Source:[Router's external IP] Destination:10.0.0.2 Length:72 TOS:0x00 Protocol:ICMP Service:Unknown
In:eth0 Out: Port:80 Source:[Router's external IP] Destination:10.0.0.2 Length:72 TOS:0x00 Protocol:ICMP Service:HTTP
In:eth0 Out: Port:995 Source:[Router's external IP] Destination:10.0.0.2 Length:72 TOS:0x00 Protocol:ICMP Service:Unknown
In:eth0 Out: Port:80 Source:[Router's external IP] Destination:10.0.0.2 Length:72 TOS:0x00 Protocol:ICMP Service:HTTP
In:eth0 Out: Port:995 Source:[Router's external IP] Destination:10.0.0.2 Length:72 TOS:0x00 Protocol:ICMP Service:Unknown


I've got a few machines behind a linksys router which is performing NAT & DHCP for the local network.  My understanding of NAT was that an external host cannot initiate a connection to (or ping) a internal IP.  Is this something I'm doing without realising it?

---

