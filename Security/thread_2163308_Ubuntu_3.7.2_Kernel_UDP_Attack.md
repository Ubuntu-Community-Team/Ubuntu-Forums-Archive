---
title: "Ubuntu 3.7.2 Kernel UDP Attack?"
date: 2013-07-17
forum: Security
---

### Post by own3mall on 2013-07-17
Hi guys, my server went down from about 6:30 to 7:30 PM.  At this time, I was unable to access anything.  My server bandwidth charts were showing 100MB outgoing traffic.  I'm not sure what was using all of my bandwidth, but it looks like I was under attack.  My syslog contains several entries like this from that time period:

```

Jul 17 18:36:09 ht kernel: [641009.991280] UDP: bad checksum. From 220.110.189.98:19 to 216.230.226.187:21143 ulen 3189
Jul 17 18:36:09 ht kernel: [641010.256828] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:21143 ulen 2474
Jul 17 18:36:11 ht kernel: [641012.847521] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:21143 ulen 4292
Jul 17 18:36:17 ht kernel: [641018.157584] UDP: bad checksum. From 220.110.189.98:19 to 216.230.226.187:21143 ulen 1895
Jul 17 18:36:18 ht kernel: [641019.180909] UDP: bad checksum. From 220.110.189.98:19 to 216.230.226.187:21143 ulen 2618
Jul 17 18:36:26 ht kernel: [641027.785100] UDP: bad checksum. From 114.179.71.58:19 to 216.230.226.187:21143 ulen 1490
Jul 17 18:36:28 ht kernel: [641029.440581] UDP: bad checksum. From 114.179.71.58:19 to 216.230.226.187:21143 ulen 2694
Jul 17 18:36:28 ht kernel: [641029.611404] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:23489 ulen 1750
Jul 17 18:36:29 ht kernel: [641030.307695] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:23489 ulen 2502
Jul 17 18:36:30 ht kernel: [641031.082094] UDP: bad checksum. From 50.62.144.189:19 to 216.230.226.187:23489 ulen 1495
Jul 17 18:36:30 ht kernel: [641031.643682] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:21143 ulen 3444
Jul 17 18:36:39 ht kernel: [641039.931495] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:23489 ulen 2238
Jul 17 18:36:48 ht kernel: [641049.739040] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:23489 ulen 2093
Jul 17 18:36:50 ht kernel: [641051.589232] UDP: bad checksum. From 184.168.64.172:19 to 216.230.226.187:23489 ulen 1491
Jul 17 18:37:03 ht kernel: [641064.703937] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:21143 ulen 5572
Jul 17 18:37:39 ht kernel: [641100.221030] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:23489 ulen 2161
Jul 17 18:37:42 ht kernel: [641102.866090] UDP: bad checksum. From 162.202.238.167:19 to 216.230.226.187:21143 ulen 1499
Jul 17 18:37:42 ht kernel: [641102.912391] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:21143 ulen 4044
Jul 17 18:37:43 ht kernel: [641104.375212] UDP: bad checksum. From 173.19.235.139:19 to 216.230.226.187:21143 ulen 1493
Jul 17 18:37:57 ht kernel: [641118.124736] UDP: bad checksum. From 172.7.154.89:19 to 216.230.226.187:21143 ulen 1500
Jul 17 18:38:05 ht kernel: [641126.545940] UDP: bad checksum. From 195.77.92.227:19 to 216.230.226.187:23489 ulen 1491
Jul 17 18:38:19 ht kernel: [641139.605315] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:23489 ulen 1964
Jul 17 18:38:19 ht kernel: [641139.645961] UDP: bad checksum. From 220.110.189.98:19 to 216.230.226.187:21143 ulen 2887
Jul 17 18:38:19 ht kernel: [641139.960215] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:21143 ulen 1945
Jul 17 18:38:29 ht kernel: [641150.432981] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:21143 ulen 2542
Jul 17 18:38:39 ht kernel: [641160.026517] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:21143 ulen 1973
Jul 17 18:38:40 ht kernel: [641160.825408] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:23489 ulen 2814
Jul 17 18:38:48 ht kernel: [641169.260246] UDP: bad checksum. From 184.168.72.227:19 to 216.230.226.187:21143 ulen 1494
Jul 17 18:38:49 ht kernel: [641169.648735] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:21143 ulen 1730
Jul 17 18:38:49 ht kernel: [641169.673924] UDP: bad checksum. From 212.76.93.231:19 to 216.230.226.187:21143 ulen 1498
Jul 17 18:38:50 ht kernel: [641170.744423] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:23489 ulen 2497
Jul 17 18:38:56 ht kernel: [641177.134341] UDP: bad checksum. From 114.179.71.58:19 to 216.230.226.187:21143 ulen 1545
Jul 17 18:38:57 ht kernel: [641177.766326] UDP: bad checksum. From 75.25.155.205:19 to 216.230.226.187:21143 ulen 1487
Jul 17 18:38:58 ht kernel: [641178.732723] UDP: bad checksum. From 114.179.71.58:19 to 216.230.226.187:21143 ulen 2661
Jul 17 18:39:00 ht kernel: [641180.573311] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:23489 ulen 2352

```

Does this look like a DDoS attack of some sort?  Is there anything I can do to prevent this?

---

### Post by wildmanne39 on 2013-07-17
*Thread moved to **Security Discussions**.*

---

### Post by Hungry Man on 2013-07-18
How odd. The requests seem to be going to/ coming from [http://www.visualsatsystem.com/visualsat/](http://www.visualsatsystem.com/visualsat/)

---

### Post by samiux on 2013-07-19
> **own3mall said:**
> Hi guys, my server went down from about 6:30 to 7:30 PM.  At this time, I was unable to access anything.  My server bandwidth charts were showing 100MB outgoing traffic.  I'm not sure what was using all of my bandwidth, but it looks like I was under attack.  My syslog contains several entries like this from that time period:

```

Jul 17 18:36:09 ht kernel: [641009.991280] UDP: bad checksum. From 220.110.189.98:19 to 216.230.226.187:21143 ulen 3189
Jul 17 18:36:09 ht kernel: [641010.256828] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:21143 ulen 2474
Jul 17 18:36:11 ht kernel: [641012.847521] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:21143 ulen 4292
Jul 17 18:36:17 ht kernel: [641018.157584] UDP: bad checksum. From 220.110.189.98:19 to 216.230.226.187:21143 ulen 1895
Jul 17 18:36:18 ht kernel: [641019.180909] UDP: bad checksum. From 220.110.189.98:19 to 216.230.226.187:21143 ulen 2618
Jul 17 18:36:26 ht kernel: [641027.785100] UDP: bad checksum. From 114.179.71.58:19 to 216.230.226.187:21143 ulen 1490
Jul 17 18:36:28 ht kernel: [641029.440581] UDP: bad checksum. From 114.179.71.58:19 to 216.230.226.187:21143 ulen 2694
Jul 17 18:36:28 ht kernel: [641029.611404] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:23489 ulen 1750
Jul 17 18:36:29 ht kernel: [641030.307695] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:23489 ulen 2502
Jul 17 18:36:30 ht kernel: [641031.082094] UDP: bad checksum. From 50.62.144.189:19 to 216.230.226.187:23489 ulen 1495
Jul 17 18:36:30 ht kernel: [641031.643682] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:21143 ulen 3444
Jul 17 18:36:39 ht kernel: [641039.931495] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:23489 ulen 2238
Jul 17 18:36:48 ht kernel: [641049.739040] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:23489 ulen 2093
Jul 17 18:36:50 ht kernel: [641051.589232] UDP: bad checksum. From 184.168.64.172:19 to 216.230.226.187:23489 ulen 1491
Jul 17 18:37:03 ht kernel: [641064.703937] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:21143 ulen 5572
Jul 17 18:37:39 ht kernel: [641100.221030] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:23489 ulen 2161
Jul 17 18:37:42 ht kernel: [641102.866090] UDP: bad checksum. From 162.202.238.167:19 to 216.230.226.187:21143 ulen 1499
Jul 17 18:37:42 ht kernel: [641102.912391] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:21143 ulen 4044
Jul 17 18:37:43 ht kernel: [641104.375212] UDP: bad checksum. From 173.19.235.139:19 to 216.230.226.187:21143 ulen 1493
Jul 17 18:37:57 ht kernel: [641118.124736] UDP: bad checksum. From 172.7.154.89:19 to 216.230.226.187:21143 ulen 1500
Jul 17 18:38:05 ht kernel: [641126.545940] UDP: bad checksum. From 195.77.92.227:19 to 216.230.226.187:23489 ulen 1491
Jul 17 18:38:19 ht kernel: [641139.605315] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:23489 ulen 1964
Jul 17 18:38:19 ht kernel: [641139.645961] UDP: bad checksum. From 220.110.189.98:19 to 216.230.226.187:21143 ulen 2887
Jul 17 18:38:19 ht kernel: [641139.960215] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:21143 ulen 1945
Jul 17 18:38:29 ht kernel: [641150.432981] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:21143 ulen 2542
Jul 17 18:38:39 ht kernel: [641160.026517] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:21143 ulen 1973
Jul 17 18:38:40 ht kernel: [641160.825408] UDP: bad checksum. From 221.224.120.187:19 to 216.230.226.187:23489 ulen 2814
Jul 17 18:38:48 ht kernel: [641169.260246] UDP: bad checksum. From 184.168.72.227:19 to 216.230.226.187:21143 ulen 1494
Jul 17 18:38:49 ht kernel: [641169.648735] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:21143 ulen 1730
Jul 17 18:38:49 ht kernel: [641169.673924] UDP: bad checksum. From 212.76.93.231:19 to 216.230.226.187:21143 ulen 1498
Jul 17 18:38:50 ht kernel: [641170.744423] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:23489 ulen 2497
Jul 17 18:38:56 ht kernel: [641177.134341] UDP: bad checksum. From 114.179.71.58:19 to 216.230.226.187:21143 ulen 1545
Jul 17 18:38:57 ht kernel: [641177.766326] UDP: bad checksum. From 75.25.155.205:19 to 216.230.226.187:21143 ulen 1487
Jul 17 18:38:58 ht kernel: [641178.732723] UDP: bad checksum. From 114.179.71.58:19 to 216.230.226.187:21143 ulen 2661
Jul 17 18:39:00 ht kernel: [641180.573311] UDP: bad checksum. From 119.145.97.107:19 to 216.230.226.187:23489 ulen 2352

```

Does this look like a DDoS attack of some sort?  Is there anything I can do to prevent this?

@own3mall,

Yes, your server is under DDoS attack via the network layer.  You can prevent from being attacked by blocking from the source port 19 and type UDP to the destination port 1024-65535 and type UDP.

Good luck.

Samiux

---

