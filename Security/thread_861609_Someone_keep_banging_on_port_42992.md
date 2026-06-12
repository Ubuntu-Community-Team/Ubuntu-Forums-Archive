---
title: "Someone keep banging on port 42992"
date: 2008-07-16
forum: Security
---

### Post by DarkDancer on 2008-07-16
Anyone know what's up with that?

---

### Post by Dr Small on 2008-07-16
[quote=Sherlock Holmes]It is a capital mistake to theorize before you have all the evidence. It biases the judgment.[/quote]

:)

---

### Post by DarkDancer on 2008-07-16
Thanks, um, how is that urbane to my question?

---

### Post by lisati on 2008-07-16
> **Dr Small said:**
> :)

> **DarkDancer said:**
> Thanks, um, how is that urbane to my question?

Dr Small: Are you able to offer some evidence for us to ponder, e.g. copies of logs? It would help us avoid unhelpful theorizing.

---

### Post by DarkDancer on 2008-07-16
> Time:Jul 16 18:23:48 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.90.51 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 18:25:33 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.90.58 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 18:27:42 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.91.39 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 18:29:56 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.90.82 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 18:32:06 Direction: Unknown In:eth0 Out: Port:42992 Source:38.107.163.18 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 18:39:06 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.88.210 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 18:41:24 Direction: Unknown In:eth0 Out: Port:42992 Source:38.107.162.241 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 18:46:36 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.90.69 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 18:52:51 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.90.48 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 18:58:19 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.89.187 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 19:01:10 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.91.2 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 19:05:28 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.90.82 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 19:09:29 Direction: Unknown In:eth0 Out: Port:42992 Source:38.107.161.160 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 19:18:37 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.91.54 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 19:21:44 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.89.204 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 19:26:16 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.90.50 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 19:30:58 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.91.59 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 19:33:18 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.91.12 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 19:35:41 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.90.48 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 19:38:13 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.91.14 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 19:46:02 Direction: Unknown In:eth0 Out: Port:42992 Source:38.107.163.32 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 19:48:47 Direction: Unknown In:eth0 Out: Port:42992 Source:72.172.90.89 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 19:51:25 Direction: Unknown In:eth0 Out: Port:42992 Source:38.107.163.35 Destination:192.168.1.2 Length:60 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jul 16 20:53:26 Direction: Unknown In:eth0 Out: Port:46161 Source:60.237.6.184 Destination:192.168.1.2 Length:44 TOS:0x00 Protocol:TCP Service:Unknown

It seems to have stopped now though.

---

### Post by Keeters on 2008-07-17
If you really wanted to know what that is all about I would put a packet sniffer out there and grab the payloads off the attempts. Then after that run it through an IDS and see if it matches any signatures. If not, well... go figure.

---

