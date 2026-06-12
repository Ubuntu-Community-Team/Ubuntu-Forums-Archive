---
title: "firestarter keeps blocking ip's"
date: 2011-03-08
forum: Security
---

### Post by heinns on 2011-03-08
Ok sorry if this is in the wrong section but im having a bit of a problem with Firestarter, i have Transmission opened and i am downloading a movie but when i check Firestarter i see hundreds and hundreds of Ip's that are blocked, and like 10ip's every second that get blocked.

How do i fix this?

[PHP]Time:Mar  9 12:56:05 Direction: Unknown In:eth0 Out: Port:51413 Source:60.242.42.144 Destination:10.0.0.1 Length:90 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar  9 12:56:05 Direction: Unknown In:eth0 Out: Port:51413 Source:2.85.32.40 Destination:10.0.0.1 Length:64 TOS:0x00 Protocol:TCP Service:Unknown
Time:Mar  9 12:56:06 Direction: Unknown In:eth0 Out: Port:51413 Source:203.122.198.209 Destination:10.0.0.1 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Mar  9 12:56:06 Direction: Unknown In:eth0 Out: Port:51413 Source:2.85.32.40 Destination:10.0.0.1 Length:64 TOS:0x00 Protocol:TCP Service:Unknown
Time:Mar  9 12:56:09 Direction: Unknown In:eth0 Out: Port:51413 Source:203.122.198.209 Destination:10.0.0.1 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Mar  9 12:56:09 Direction: Unknown In:eth0 Out: Port:51413 Source:99.249.215.216 Destination:10.0.0.1 Length:95 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar  9 12:56:11 Direction: Unknown In:eth0 Out: Port:51413 Source:99.100.147.93 Destination:10.0.0.1 Length:95 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar  9 12:56:11 Direction: Unknown In:eth0 Out: Port:51413 Source:89.216.149.137 Destination:10.0.0.1 Length:95 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar  9 12:56:11 Direction: Unknown In:eth0 Out: Port:51413 Source:99.231.253.145 Destination:10.0.0.1 Length:64 TOS:0x00 Protocol:TCP Service:Unknown
Time:Mar  9 12:56:12 Direction: Unknown In:eth0 Out: Port:51413 Source:86.145.239.101 Destination:10.0.0.1 Length:86 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar  9 12:56:12 Direction: Unknown In:eth0 Out: Port:51413 Source:213.166.185.171 Destination:10.0.0.1 Length:58 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar  9 12:56:12 Direction: Unknown In:eth0 Out: Port:51413 Source:213.166.185.171 Destination:10.0.0.1 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Mar  9 12:56:15 Direction: Unknown In:eth0 Out: Port:51413 Source:213.166.185.171 Destination:10.0.0.1 Length:58 TOS:0x00 Protocol:UDP Service:Unknown[/PHP]

---

### Post by Sef on 2011-03-09
Remove Firestarter and use UFW because the former is not longer being improved, while the latter is being improved. UFW is in the repositories.

---

### Post by wacky_sung on 2011-03-09
Actually what you saw is kinda common especially you are using BT. Restart your system and it will be able to clear away all half-open connection to system.

---

