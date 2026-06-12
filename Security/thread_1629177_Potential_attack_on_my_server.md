---
title: "Potential attack on my server"
date: 2010-11-23
forum: Security
---

### Post by helyos on 2010-11-23
Hi there,
One of my servers is leased from OVH network and since this weekend my traffic has gone mad. I think someone is flooding us. I have installed on server firestarter and in logs i can see many connections blocked on port 53 and port 80. The weird problem is that I don't have a dns server installed on this machine.

Here is some of our log:

```
Time:Nov 23 18:57:03 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:04 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:04 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:07 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:07 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:13 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:13 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:25 Direction: Inbound In:eth0 Out: Port:80 Source:109.96.50.97 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:25 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:26 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:26 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:28 Direction: Inbound In:eth0 Out: Port:80 Source:109.96.50.97 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:28 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:29 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:29 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:30 Direction: Inbound In:eth0 Out: Port:80 Source:109.96.50.97 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:30 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:33 Direction: Inbound In:eth0 Out: Port:80 Source:109.96.50.97 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:33 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:35 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:35 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:39 Direction: Inbound In:eth0 Out: Port:80 Source:109.96.50.97 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:39 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:48 Direction: Inbound In:eth0 Out: Port:80 Source:109.96.220.30 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:48 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:51 Direction: Inbound In:eth0 Out: Port:80 Source:109.96.220.30 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:51 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:52 Direction: Inbound In:eth0 Out: Port:80 Source:109.166.143.153 Destination:91.121.74.208 Length:64 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:52 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:55 Direction: Inbound In:eth0 Out: Port:80 Source:109.166.143.153 Destination:91.121.74.208 Length:64 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:55 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:57 Direction: Inbound In:eth0 Out: Port:80 Source:109.96.220.30 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:57 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:57:58 Direction: Inbound In:eth0 Out: Port:80 Source:109.166.143.153 Destination:91.121.74.208 Length:64 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:57:58 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:58:07 Direction: Inbound In:eth0 Out: Port:80 Source:109.166.143.153 Destination:91.121.74.208 Length:64 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:58:07 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:58:14 Direction: Inbound In:eth0 Out: Port:80 Source:109.166.143.153 Destination:91.121.74.208 Length:64 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:58:14 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:58:20 Direction: Inbound In:eth0 Out: Port:80 Source:109.166.143.153 Destination:91.121.74.208 Length:64 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:58:20 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:58:22 Direction: Inbound In:eth0 Out: Port:135 Source:91.83.127.50 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:DCOM-scm
Time:Nov 23 18:58:22 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:58:25 Direction: Inbound In:eth0 Out: Port:135 Source:91.83.127.50 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:DCOM-scm
Time:Nov 23 18:58:25 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:58:34 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:58:34 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:58:37 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:58:37 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:58:43 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:58:43 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:58:46 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:58:46 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:58:52 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:58:52 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:04 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:04 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:07 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:07 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:13 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:13 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:15 Direction: Inbound In:eth0 Out: Port:80 Source:178.248.144.105 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:15 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:18 Direction: Inbound In:eth0 Out: Port:80 Source:178.248.144.105 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:18 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:24 Direction: Inbound In:eth0 Out: Port:80 Source:178.248.144.105 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:24 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:26 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:26 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:29 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:29 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:30 Direction: Inbound In:eth0 Out: Port:80 Source:109.97.91.7 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:30 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:33 Direction: Inbound In:eth0 Out: Port:80 Source:109.97.91.7 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:33 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:35 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:35 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:39 Direction: Inbound In:eth0 Out: Port:80 Source:109.97.91.7 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:39 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:51 Direction: Inbound In:eth0 Out: Port:80 Source:109.97.91.7 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:51 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:52 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:52 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:54 Direction: Inbound In:eth0 Out: Port:80 Source:109.97.91.7 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:54 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:55 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:55 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 18:59:58 Direction: Inbound In:eth0 Out: Port:80 Source:178.248.144.105 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 18:59:58 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:00:00 Direction: Inbound In:eth0 Out: Port:80 Source:109.97.91.7 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:00:00 Direction: Inbound In:eth0 Out: Port:80 Source:178.248.144.105 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:00:00 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:00:01 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:00:01 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:00:06 Direction: Inbound In:eth0 Out: Port:80 Source:178.248.144.105 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:00:06 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:00:13 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:00:13 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:00:16 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:00:16 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:00:22 Direction: Inbound In:eth0 Out: Port:80 Source:178.156.168.65 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:00:22 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:00:50 Direction: Inbound In:eth0 Out: Port:80 Source:178.248.144.105 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:00:50 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:00:53 Direction: Inbound In:eth0 Out: Port:80 Source:178.248.144.105 Destination:91.121.74.208 Length:52 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:00:53 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:00:59 Direction: Inbound In:eth0 Out: Port:80 Source:178.248.144.105 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:00:59 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:01:07 Direction: Inbound In:eth0 Out: Port:80 Source:109.96.50.97 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:01:07 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:01:10 Direction: Inbound In:eth0 Out: Port:80 Source:109.96.50.97 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:01:10 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:01:16 Direction: Inbound In:eth0 Out: Port:80 Source:109.96.50.97 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:01:16 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:01:18 Direction: Inbound In:eth0 Out: Port:80 Source:109.96.50.97 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:01:18 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:01:21 Direction: Inbound In:eth0 Out: Port:80 Source:109.96.50.97 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:01:21 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
Time:Nov 23 19:01:27 Direction: Inbound In:eth0 Out: Port:80 Source:109.96.50.97 Destination:91.121.74.208 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Nov 23 19:01:27 Direction: Inbound In:eth0 Out: Port:53 Source:95.143.192.164 Destination:91.121.74.208 Length:43 TOS:0x00 Protocol:UDP Service:DNS
```

What can i do to minimize these attacks, because they are overloading server!

Thank you so much in advance!

---

### Post by HermanAB on 2010-11-24
Howdy,

I would enable an iptables rate limit filter.

[http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)

---

### Post by CharlesA on 2010-11-24
What Herman said.

I'd suggest just using straight iptables or ufw instead of firestarter.

---

### Post by emiller12345 on 2010-11-24
This is a niffty little command to determine the frequency of incidents of source ip's from your log. It's only looking at Port 80 (http) and Port 53 (dns)
```
cat log.txt | grep -e "Port:80" -e "Port:53" | awk '{print $9}' | awk -F: '{print $2}' | sort | uniq -c | sort -r -n
```Output: frequency IP
```
     60 95.143.192.164
     23 178.156.168.65
     11 109.96.50.97
      9 178.248.144.105
      6 109.97.91.7
      6 109.166.143.153
      3 109.96.220.30

```

---

### Post by CharlesA on 2010-11-24
> **emiller12345 said:**
> This is a niffty little command to determine the frequency of incidents of source ip's from your log. It's only looking at Port 80 (http) and Port 53 (dns)
```
cat log.txt | grep -e "Port:80" -e "Port:53" | awk '{print $9}' | awk -F: '{print $2}' | sort | uniq -c | sort -r -n
```


That's a nice bit of code.

Couldn't you use cat /var/log/auth.log instead of a different file?

---

### Post by helyos on 2010-11-24
I think there was a "DNS Amplification Attack" coming from 95.143.192.164 . I contacted their support and now everything stopped. 
I have blocked port 80 too, for a while.

Now i am trying to understand how ip tables work and maybe use them instead of my firewall.

---

### Post by CharlesA on 2010-11-24
> **helyos said:**
> 
Now i am trying to understand how ip tables work and maybe use them instead of my firewall.

iptables is the firewall. Firestarter is just a frontend for it.

Check this page out: [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by endotherm on 2010-11-24
> **helyos said:**
> I think there was a "DNS Amplification Attack" coming from 95.143.192.164 . I contacted their support and now everything stopped. 
I have blocked port 80 too, for a while.

Now i am trying to understand how ip tables work and maybe use them instead of my firewall.

actually the firewall thing is a little complicatexd.

the actual firewall is called 'netfilter' and is part of the kernel. IPTables is a front-end for configuring netfilter. UFW and firestarter are a frontend for configuring IPTables, and Gufw is a frontend for configuring UFW. 

so whatever tools you use, the firewall is the same, but the tools determine teh quality of the rules added to netfilter, so some are recommended and others not. Firestarter is a largely dead project, so no fixes or improvements in some years. thats why people recommend gufw.

firestarter and GUFW are configuration utilities not the firewall itself. that means that you only ever need to start them when you wish to make a change to the firewalll ruleset. no point in autostarting them or having them running all the time. the firewall iteslf is already running with the ruleset you already applied, so you shouldn't need to use them much.

---

### Post by emiller12345 on 2010-11-24
> **CharlesA said:**
> That's a nice bit of code.
  
 Couldn't you use cat /var/log/auth.log instead of a different file?
  
 Yeah that would work better. I wasn't sure where that data came from,  but I use that kind of command all the time for looking at network  stats.

---

### Post by CharlesA on 2010-11-24
> **emiller12345 said:**
> Yeah that would work better. I wasn't sure where that data came from,  but I use that kind of command all the time for looking at network  stats.
It's going to be going into my toolbox. :)

---

