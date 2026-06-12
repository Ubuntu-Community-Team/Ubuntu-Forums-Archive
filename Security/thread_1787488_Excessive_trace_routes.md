---
title: "Excessive trace routes"
date: 2011-06-21
forum: Security
---

### Post by jmore9 on 2011-06-21
Hello !

I have been seeing the following quite a bit:

Time:Jun 21 05:11:37 Direction: Unknown In:eth0 Out: Port:33445 Source:66.150.8.24 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:43 Direction: Unknown In:eth0 Out: Port:33444 Source:66.150.8.8 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:45 Direction: Unknown In:eth0 Out: Port:33445 Source:66.150.8.24 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:45 Direction: Unknown In:eth0 Out: Port:33444 Source:66.150.8.8 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:47 Direction: Unknown In:eth0 Out: Port:33445 Source:66.150.8.24 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:47 Direction: Unknown In:eth0 Out: Port:33444 Source:66.150.8.8 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:49 Direction: Unknown In:eth0 Out: Port:33445 Source:66.150.8.24 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:49 Direction: Unknown In:eth0 Out: Port:33444 Source:66.150.8.8 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:51 Direction: Unknown In:eth0 Out: Port:33445 Source:66.150.8.24 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:51 Direction: Unknown In:eth0 Out: Port:33444 Source:66.150.8.8 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:53 Direction: Unknown In:eth0 Out: Port:33440 Source:66.150.8.20 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:53 Direction: Unknown In:eth0 Out: Port:33444 Source:66.150.8.8 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:55 Direction: Unknown In:eth0 Out: Port:33440 Source:66.150.8.20 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:55 Direction: Unknown In:eth0 Out: Port:33444 Source:66.150.8.8 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:57 Direction: Unknown In:eth0 Out: Port:33440 Source:66.150.8.20 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:57 Direction: Unknown In:eth0 Out: Port:33444 Source:66.150.8.8 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Jun 21 05:11:59 Direction: Unknown In:eth0 Out: Port:33440 Source:66.150.8.20 Destination:198.77.49.67 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute

Also the same thing using 64.94.179.12,64.94.179.52 on earlier events.  I had nothing going except watching youtube videos.  Also they are pretty one right after another so would that not be considered a DOS ?  The earlier one was exactly the same format.

Anyone got any ideas ?

---

### Post by jmore9 on 2011-06-21
I also noticed that Rdesktop had been installed.  Now i do not connect to any windows machines that i know of with this machine.  Running 11.04.  So i uninstalled it.   Doesn't seem to make any difference.

---

### Post by jmore9 on 2011-06-21
And if you go here you see that ip has a history of problems :

[http://www.bizimbal.com/odb/details.html?id=486703](http://www.bizimbal.com/odb/details.html?id=486703)

---

