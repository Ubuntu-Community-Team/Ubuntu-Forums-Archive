---
title: "Ubuntu 10.04 server trying to constantly access ip address via SSL"
date: 2011-11-09
forum: Security
---

### Post by scrummie02 on 2011-11-09
I have an openbsd pf firewall running filtering traffic.  I have an Unbuntu server running in the DMZ that is used for web development most notably RoR with Apache/Passenger.  I log all outbound traffic from the DMZ so I can see what traffic is coming from my network.  I noticed this in my TCPDump files coming from my ubuntu server about every second.


Nov 09 14:08:53.501303 rule 28/(match) pass in on fxp0: 192.168.100.53.55370 > 65.98.23.210.443: S 3356665833:3356665833(0) win 5840 <mss 1460,sackOK,timestamp 85230386 0,nop,wscale 5> (DF)
Nov 09 14:09:09.212927 rule 28/(match) pass in on fxp0: 192.168.100.53.55371 > 65.98.23.210.443: S 3611450337:3611450337(0) win 5840 <mss 1460,sackOK,timestamp 85231957 0,nop,wscale 5> (DF)
Nov 09 14:09:24.735394 rule 28/(match) pass in on fxp0: 192.168.100.53.55372 > 65.98.23.210.443: S 3853783363:3853783363(0) win 5840 <mss 1460,sackOK,timestamp 85233509 0,nop,wscale 5> (DF)
Nov 09 14:09:40.056057 rule 28/(match) pass in on fxp0: 192.168.100.53.55373 > 65.98.23.210.443: S 4081071978:4081071978(0) win 5840 <mss 1460,sackOK,timestamp 85235041 0,nop,wscale 5> (DF)
Nov 09 14:09:55.568317 rule 28/(match) pass in on fxp0: 192.168.100.53.55374 > 65.98.23.210.443: S 42446464:42446464(0) win 5840 <mss 1460,sackOK,timestamp 85236593 0,nop,wscale 5> (DF)
Nov 09 14:10:11.132444 rule 28/(match) pass in on fxp0: 192.168.100.53.55375 > 65.98.23.210.443: S 282463882:282463882(0) win 5840 <mss 1460,sackOK,timestamp 85238149 0,nop,wscale 5> (DF)
Nov 09 14:10:26.657213 rule 28/(match) pass in on fxp0: 192.168.100.53.55376 > 65.98.23.210.443: S 524442506:524442506(0) win 5840 <mss 1460,sackOK,timestamp 85239702 0,nop,wscale 5> (DF)
Nov 09 14:10:42.308995 rule 28/(match) pass in on fxp0: 192.168.100.53.55379 > 65.98.23.210.443: S 761476142:761476142(0) win 5840 <mss 1460,sackOK,timestamp 85241267 0,nop,wscale 5> (DF)
Nov 09 14:10:57.735054 rule 28/(match) pass in on fxp0: 192.168.100.53.55380 > 65.98.23.210.443: S 1012468045:1012468045(0) win 5840 <mss 1460,sackOK,timestamp 85242809 0,nop,wscale 5> (DF)
Nov 09 14:11:13.259416 rule 28/(match) pass in on fxp0: 192.168.100.53.55381 > 65.98.23.210.443: S 1250519717:1250519717(0) win 5840 <mss 1460,sackOK,timestamp 85244362 0,nop,wscale 5> (DF)
Nov 09 14:11:28.767281 rule 28/(match) pass in on fxp0: 192.168.100.53.55382 > 65.98.23.210.443: S 1494512084:1494512084(0) win 5840 <mss 1460,sackOK,timestamp 85245913 0,nop,wscale 5> (DF)
Nov 09 14:11:44.235112 rule 28/(match) pass in on fxp0: 192.168.100.53.55383 > 65.98.23.210.443: S 1739389565:1739389565(0) win 5840 <mss 1460,sackOK,timestamp 85247460 0,nop,wscale 5> (DF)
Nov 09 14:11:59.323744 rule 28/(match) pass in on fxp0: 192.168.100.53.55384 > 65.98.23.210.443: S 1965481506:1965481506(0) win 5840 <mss 1460,sackOK,timestamp 85248968 0,nop,wscale 5> (DF)


Basically this is showing ssl traffic leaving from my ubuntu server go to 65.98.23.210.  When I try to browse the site nothing really shows up, there is a webserver running but no permissions to the page.

Is this IP address associated with ubuntu some way?  Like is it an apt source.

SSH access is disabled from the outside so if someone got in and implanted something to beacon home they must have gotten there via a venerability in the web server or code.

---

### Post by secret resistor on 2011-11-09
The SSL certificate is for *.mobilepcmonitor.com, which as the name suggests appears to be some kind of a monitoring service.

---

### Post by scrummie02 on 2011-11-09
> **secret resistor said:**
> The SSL certificate is for *.mobilepcmonitor.com, which as the name suggests appears to be some kind of a monitoring service.

Yep, you are correct.  Someone installed it on the node so they could monitor it.  I tracked down who it was.  Thanks.

---

