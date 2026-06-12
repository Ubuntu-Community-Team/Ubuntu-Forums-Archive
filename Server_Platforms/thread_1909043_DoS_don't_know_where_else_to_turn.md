---
title: "DoS? don't know where else to turn"
date: 2012-01-14
forum: Server Platforms
---

### Post by rebeltaz on 2012-01-14
I am running a forum on my web site and I believe I have *<snip> *someone off. This morning my webserver was not responding, so why I worked on it, I started a python server on another machine to serve up a "please stand by" page. 

That was when I immediately saw this:

```

Serving HTTP on 0.0.0.0 port 8000 ...
188.92.76.217 - - [14/Jan/2012 12:36:29] code 404, message File not found
188.92.76.217 - - [14/Jan/2012 12:36:34] "GET /phpBB3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
188.92.76.217 - - [14/Jan/2012 12:36:39] code 404, message File not found
188.92.76.217 - - [14/Jan/2012 12:36:44] "GET /phpBB3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
188.92.76.217 - - [14/Jan/2012 12:36:49] code 404, message File not found
188.92.76.217 - - [14/Jan/2012 12:36:54] "GET /phpBB3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
h-130-96.cssgroup.lv - - [14/Jan/2012 12:36:54] code 404, message File not found
h-130-96.cssgroup.lv - - [14/Jan/2012 12:36:54] "GET /phpBB3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
188.92.76.217 - - [14/Jan/2012 12:36:59] code 404, message File not found
188.92.76.217 - - [14/Jan/2012 12:37:04] "GET /phpbb3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:04] code 404, message File not found
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:04] "GET /phpBB3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:04] code 404, message File not found
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:05] "GET /phpBB3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:05] code 404, message File not found
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:05] "GET /phpBB3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
188.92.76.217 - - [14/Jan/2012 12:37:10] code 404, message File not found
188.92.76.217 - - [14/Jan/2012 12:37:15] "GET /phpbb3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
188.92.76.217 - - [14/Jan/2012 12:37:20] code 404, message File not found
188.92.76.217 - - [14/Jan/2012 12:37:25] "GET /phpBB3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:25] code 404, message File not found
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:25] "GET /phpbb3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:25] code 404, message File not found
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:25] "GET /phpbb3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:25] code 404, message File not found
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:25] "GET /phpbb3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:25] code 404, message File not found
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:25] "GET /phpBB3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:25] code 404, message File not found
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:25] "GET /phpbb3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
188.92.76.217 - - [14/Jan/2012 12:37:30] code 404, message File not found
188.92.76.217 - - [14/Jan/2012 12:37:35] "GET /phpbb3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
188.92.76.217 - - [14/Jan/2012 12:37:40] code 404, message File not found
188.92.76.217 - - [14/Jan/2012 12:37:45] "GET /phpbb3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:45] code 404, message File not found
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:45] "GET /phpBB3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:45] code 404, message File not found
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:45] "GET /phpbb3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:45] code 404, message File not found
h-130-96.cssgroup.lv - - [14/Jan/2012 12:37:45] "GET /phpBB3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
188.92.76.217 - - [14/Jan/2012 12:37:50] code 404, message File not found
188.92.76.217 - - [14/Jan/2012 12:37:55] "GET /phpBB3/posting.php?mode=post&f=5 HTTP/1.0" 404 -
188.92.76.217 - - [14/Jan/2012 12:38:00] code 404, message File not found
188.92.76.217 - - [14/Jan/2012 12:38:05] "GET /phpBB3/posting.php?mode=post&f=5 HTTP/1.0" 404 -

```

Apparently, sever systems are attempting to access a page from within that forum. SO I ran a tcpdump on that interface and found this:

```

tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
12:45:42.175323 IP 192.168.1.15.55824 > 113.11.96.130.25182: Flags [S], seq 1926908240, win 5840, options [mss 1460,sackOK,TS val 320513477 ecr 0,nop,wscale 6], length 0
12:45:42.395322 ARP, Request who-has 192.168.1.250 tell 192.168.1.15, length 28
12:45:42.395541 ARP, Reply 192.168.1.250 is-at 08:86:3b:31:10:d6, length 46
12:45:42.779526 IP 192.168.1.15.5353 > 224.0.0.251.5353: 0 PTR (QM)? 217.76.92.188.in-addr.arpa. (44)
12:45:42.816976 IP 113.11.126.77 > 192.168.1.15: ICMP time exceeded in-transit, length 36
12:45:42.817226 IP 192.168.1.15.55679 > 113.11.96.130.25182: Flags [S], seq 1055715770, win 5840, options [mss 1460,sackOK,TS val 320513637 ecr 0,nop,wscale 6], length 0
12:45:42.830983 IP 192.168.1.15.8000 > 188.92.76.217.4601: Flags [P.], seq 4178209135:4178209164, ack 3732071031, win 6432, length 29
12:45:42.831136 IP 192.168.1.15.8000 > 188.92.76.217.4601: Flags [FP.], seq 29:344, ack 1, win 6432, length 315
12:45:42.831605 IP 192.168.1.15.50946 > 205.152.37.23.53: 24272+ PTR? 217.76.92.188.in-addr.arpa. (44)
12:45:42.855175 IP 205.152.37.23.53 > 192.168.1.15.50946: 24272 NXDomain 0/1/0 (110)
12:45:43.013893 IP 188.92.76.217.2179 > 192.168.1.15.8000: Flags [S], seq 2230852284, win 65535, options [mss 1452,nop,nop,sackOK], length 0
12:45:43.013921 IP 192.168.1.15.8000 > 188.92.76.217.2179: Flags [S.], seq 2795472265, ack 2230852285, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:43.026863 IP 188.92.76.217.4601 > 192.168.1.15.8000: Flags [.], ack 345, win 65191, length 0
12:45:43.026950 IP 188.92.76.217.4601 > 192.168.1.15.8000: Flags [F.], seq 1, ack 345, win 65191, length 0
12:45:43.026964 IP 192.168.1.15.8000 > 188.92.76.217.4601: Flags [.], ack 2, win 6432, length 0
12:45:43.198875 IP 188.92.76.217.2179 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:43.199414 IP 188.92.76.217.2179 > 192.168.1.15.8000: Flags [P.], seq 1:467, ack 1, win 65535, length 466
12:45:43.199430 IP 192.168.1.15.8000 > 188.92.76.217.2179: Flags [.], ack 467, win 6432, length 0
12:45:43.279090 IP 94.142.130.96.1252 > 192.168.1.15.8000: Flags [P.], seq 390579967:390580463, ack 1253188147, win 65535, length 496
12:45:43.397993 IP 188.92.76.217.2191 > 192.168.1.15.8000: Flags [S], seq 3717323566, win 65535, options [mss 1452,nop,nop,sackOK], length 0
12:45:43.659321 IP 192.168.1.15.8000 > 94.142.130.96.1252: Flags [S.], seq 1253188146, ack 390579967, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:43.748950 IP 188.92.76.217.2098 > 192.168.1.15.8000: Flags [P.], seq 4247669554:4247670060, ack 686123931, win 65535, length 506
12:45:43.823465 IP 94.142.130.96.1252 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:44.064584 IP 188.92.76.217.1419 > 192.168.1.15.8000: Flags [P.], seq 1187588388:1187588924, ack 866716572, win 65535, length 536
12:45:45.059333 IP 192.168.1.15.8000 > 188.92.76.217.1419: Flags [S.], seq 866716571, ack 1187588388, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:45.236550 IP 188.92.76.217.1419 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:45.259325 IP 192.168.1.15.8000 > 188.92.76.217.2098: Flags [S.], seq 686123930, ack 4247669554, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:45.445777 IP 188.92.76.217.2098 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:45.815322 IP 192.168.1.15.55679 > 113.11.96.130.25182: Flags [S], seq 1055715770, win 5840, options [mss 1460,sackOK,TS val 320514387 ecr 0,nop,wscale 6], length 0
12:45:46.253670 IP 188.92.76.217.2191 > 192.168.1.15.8000: Flags [S], seq 3717323566, win 65535, options [mss 1452,nop,nop,sackOK], length 0
12:45:46.253700 IP 192.168.1.15.8000 > 188.92.76.217.2191: Flags [S.], seq 13434986, ack 3717323567, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:46.457437 IP 188.92.76.217.2191 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:46.458219 IP 188.92.76.217.2191 > 192.168.1.15.8000: Flags [P.], seq 1:515, ack 1, win 65535, length 514
12:45:47.103326 IP 192.168.1.15.33656 > 114.46.207.20.9432: Flags [S], seq 2312247324, win 5840, options [mss 1460,sackOK,TS val 320514709 ecr 0,nop,wscale 6], length 0
12:45:47.859731 IP 192.168.1.15.55713 > 205.152.37.23.53: 47454+ PTR? 217.76.92.188.in-addr.arpa. (44)
12:45:47.873976 IP 205.152.37.23.53 > 192.168.1.15.55713: 47454 NXDomain 0/1/0 (110)
12:45:49.294568 IP 94.142.130.96.1252 > 192.168.1.15.8000: Flags [P.], seq 1:497, ack 1, win 65535, length 496
12:45:49.766133 IP 188.92.76.217.2098 > 192.168.1.15.8000: Flags [P.], seq 1:507, ack 1, win 65535, length 506
12:45:49.859334 IP 192.168.1.15.8000 > 188.92.76.217.2191: Flags [S.], seq 13434986, ack 3717323567, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:50.047131 IP 188.92.76.217.2191 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:50.059350 IP 192.168.1.15.8000 > 94.142.130.96.1252: Flags [S.], seq 1253188146, ack 390579967, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:50.223800 IP 94.142.130.96.1252 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:51.659340 IP 192.168.1.15.8000 > 188.92.76.217.2098: Flags [S.], seq 686123930, ack 4247669554, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:51.815334 IP 192.168.1.15.55679 > 113.11.96.130.25182: Flags [S], seq 1055715770, win 5840, options [mss 1460,sackOK,TS val 320515887 ecr 0,nop,wscale 6], length 0
12:45:51.848531 IP 188.92.76.217.2098 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:52.377207 IP 188.92.76.217.2191 > 192.168.1.15.8000: Flags [P.], seq 1:515, ack 1, win 65535, length 514
12:45:52.879621 IP 192.168.1.15.8000 > 188.92.76.217.1085: Flags [P.], seq 1406856169:1406856198, ack 1816724853, win 6432, length 29
12:45:52.879775 IP 192.168.1.15.8000 > 188.92.76.217.1085: Flags [FP.], seq 29:344, ack 1, win 6432, length 315
12:45:52.880221 IP 192.168.1.15.44134 > 205.152.37.23.53: 758+ PTR? 217.76.92.188.in-addr.arpa. (44)
12:45:52.903343 IP 205.152.37.23.53 > 192.168.1.15.44134: 758 NXDomain 0/1/0 (110)
12:45:52.964989 IP 94.142.130.96.1746 > 192.168.1.15.8000: Flags [S], seq 2568128513, win 65535, options [mss 1452,nop,nop,sackOK], length 0
12:45:52.965037 IP 192.168.1.15.8000 > 94.142.130.96.1746: Flags [S.], seq 1208232114, ack 2568128514, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:53.086260 IP 188.92.76.217.2557 > 192.168.1.15.8000: Flags [S], seq 116015990, win 65535, options [mss 1452,nop,nop,sackOK], length 0
12:45:53.086299 IP 192.168.1.15.8000 > 188.92.76.217.2557: Flags [S.], seq 1044422524, ack 116015991, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:53.094767 IP 188.92.76.217.1085 > 192.168.1.15.8000: Flags [.], ack 345, win 65191, length 0
12:45:53.094854 IP 188.92.76.217.1085 > 192.168.1.15.8000: Flags [F.], seq 1, ack 345, win 65191, length 0
12:45:53.094867 IP 192.168.1.15.8000 > 188.92.76.217.1085: Flags [.], ack 2, win 6432, length 0
12:45:53.129290 IP 94.142.130.96.1746 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:53.130288 IP 94.142.130.96.1746 > 192.168.1.15.8000: Flags [P.], seq 1:490, ack 1, win 65535, length 489
12:45:53.130322 IP 192.168.1.15.8000 > 94.142.130.96.1746: Flags [.], ack 490, win 6432, length 0
12:45:53.271940 IP 188.92.76.217.2557 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:53.272976 IP 188.92.76.217.2557 > 192.168.1.15.8000: Flags [P.], seq 1:506, ack 1, win 65535, length 505
12:45:54.227524 IP 188.92.76.217.2596 > 192.168.1.15.8000: Flags [S], seq 234672702, win 65535, options [mss 1452,nop,nop,sackOK], length 0
12:45:54.227561 IP 192.168.1.15.8000 > 188.92.76.217.2596: Flags [S.], seq 3710327572, ack 234672703, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:54.415695 IP 188.92.76.217.2596 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:54.416987 IP 188.92.76.217.2596 > 192.168.1.15.8000: Flags [P.], seq 1:511, ack 1, win 65535, length 510
12:45:55.291115 IP 192.168.1.15.4672 > 88.165.108.136.1515: UDP, length 43
12:45:55.291204 IP 192.168.1.15.4672 > 59.127.204.56.35964: UDP, length 43
12:45:55.291350 IP 192.168.1.15.4672 > 121.95.214.92.4178: UDP, length 43
12:45:55.291419 IP 192.168.1.15.4672 > 81.190.120.136.10702: UDP, length 43
12:45:55.291436 IP 192.168.1.15.4672 > 58.83.62.170.54838: UDP, length 27
12:45:55.291445 IP 192.168.1.15.4672 > 58.83.62.170.54838: UDP, length 22
12:45:55.499522 IP 192.168.1.250.9394 > 192.168.1.255.10111: UDP, length 9
12:45:55.506984 IP 121.95.214.92.4178 > 192.168.1.15.4672: UDP, length 44
12:45:55.514344 IP 88.165.108.136.1515 > 192.168.1.15.4672: UDP, length 38
12:45:55.564132 IP 81.190.120.136.10702 > 192.168.1.15.4672: UDP, length 44
12:45:56.092300 IP 188.92.76.217.1419 > 192.168.1.15.8000: Flags [P.], seq 1:537, ack 1, win 65535, length 536
12:45:56.259338 IP 192.168.1.15.8000 > 188.92.76.217.2191: Flags [S.], seq 13434986, ack 3717323567, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:56.435059 IP 188.92.76.217.2557 > 192.168.1.15.8000: Flags [P.], seq 1:506, ack 1, win 65535, length 505
12:45:56.450153 IP 188.92.76.217.2191 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:56.459339 IP 192.168.1.15.8000 > 188.92.76.217.2557: Flags [S.], seq 1044422524, ack 116015991, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:56.642611 IP 188.92.76.217.2557 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:57.357450 IP 59.127.204.56.35964 > 192.168.1.15.4672: UDP, length 44
12:45:57.405089 IP 188.92.76.217.2596 > 192.168.1.15.8000: Flags [P.], seq 1:511, ack 1, win 65535, length 510
12:45:57.907800 IP 192.168.1.15.39107 > 205.152.37.23.53: 53631+ PTR? 217.76.92.188.in-addr.arpa. (44)
12:45:57.922612 IP 205.152.37.23.53 > 192.168.1.15.39107: 53631 NXDomain 0/1/0 (110)
12:45:58.299623 IP 192.168.1.250 > 224.0.0.1: igmp query v2
12:45:58.459342 IP 192.168.1.15.8000 > 188.92.76.217.2596: Flags [S.], seq 3710327572, ack 234672703, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:58.653701 IP 188.92.76.217.2596 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:58.782742 IP 192.168.1.15.5353 > 224.0.0.251.5353: 0 PTR (QM)? 217.76.92.188.in-addr.arpa. (44)
12:45:58.971849 IP 188.92.76.217.2776 > 192.168.1.15.8000: Flags [S], seq 3795408854, win 65535, options [mss 1452,nop,nop,sackOK], length 0
12:45:58.971884 IP 192.168.1.15.8000 > 188.92.76.217.2776: Flags [S.], seq 3923858857, ack 3795408855, win 5840, options [mss 1460,nop,nop,sackOK], length 0
12:45:59.125825 IP 66.249.68.13.48138 > 192.168.1.15.8000: Flags [S], seq 747144742, win 5840, options [mss 1452,sackOK,TS val 3431641963 ecr 0,nop,wscale 6], length 0
12:45:59.125881 IP 192.168.1.15.8000 > 66.249.68.13.48138: Flags [S.], seq 3646995846, ack 747144743, win 5792, options [mss 1460,sackOK,TS val 320517714 ecr 3431641963,nop,wscale 6], length 0
12:45:59.186137 IP 188.92.76.217.2776 > 192.168.1.15.8000: Flags [.], ack 1, win 65535, length 0
12:45:59.186892 IP 188.92.76.217.2776 > 192.168.1.15.8000: Flags [P.], seq 1:487, ack 1, win 65535, length 486
12:45:59.221099 IP 66.249.68.13.48138 > 192.168.1.15.8000: Flags [.], ack 1, win 92, options [nop,nop,TS val 3431642058 ecr 320517714], length 0
12:45:59.221596 IP 66.249.68.13.48138 > 192.168.1.15.8000: Flags [P.], seq 1:326, ack 1, win 92, options [nop,nop,TS val 3431642058 ecr 320517714], length 325
12:45:59.928162 IP 66.249.68.13.48138 > 192.168.1.15.8000: Flags [P.], seq 1:326, ack 1, win 92, options [nop,nop,TS val 3431642765 ecr 320517714], length 325
12:46:00.399800 IP 192.168.1.250 > 224.0.0.1: igmp query v2
100 packets captured
100 packets received by filter
0 packets dropped by kernel

```

If this is a DoS attack, it's my first! I know this is probably not the right place to ask, but I don't know where else to go. 

Does anyone know what I can do or where I can go to ask for help on getting my system back online?

Thanks...

---

### Post by Dangertux on 2012-01-14
Ummm doesn't look like you're being attacked but it does seem like your server's resources are probably being exhausted (The crash is indicative of this).

---

### Post by cariboo on 2012-01-14
Moved to Server Platforms, as you'll probably get better help here, than in the Cafe.

---

### Post by rebeltaz on 2012-01-14
> **Dangertux said:**
> Ummm doesn't look like you're being attacked but it does seem like your server's resources are probably being exhausted (The crash is indicative of this).

It's an old system, I'll grant that, but my site does not generate this kind of traffic. I get maybe 100 hits a week!

---

### Post by |{urse on 2012-01-14
Just looks like your server is under strain. Or someone is auditing it for vulnerabilities. Since you're worried about being attacked though,you should perform a security audit. 

> sudo apt-get install w3af <--

---

### Post by rebeltaz on 2012-01-15
I just wanted to update this. Apparently an idiot or two was spamming the forum with hundreds of spam posts to one particular topic. Using the tcpdump I was able to ascertain the IP address associated with this and block it through iptables. 

I'm surprised that the Netopia router I am using doesn't have the ability to filter IP addresses itself. I guess I'll be looking for a new router. 

Thanks guys.

---

