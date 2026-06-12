---
title: "http to internet working from browser, not from command line (telnet)"
date: 2006-02-04
forum: Server Platforms
---

### Post by eudoxos on 2006-02-04
Hi everybody,

I have a breezy/dapper mix. Browsing (http) works just fine from firefox but if I do "[FONT="Fixedsys"]telnet [www.google.com](www.google.com) 80[/FONT]", it tries undefinitely.

This happens regardless of the service port: ssh is able to receive the remote machine fingerprint, but hangs after sending the password. Ssh worked under Windows, though (putty).

I have iptables flushed and ACCEPTing everything (FORWARD, INPUT, OUTPUT). I am completely clueless what is going on.

This machine is connected over WPA wireless to ADSL router, if that matters.

Thanks for any help,

Eudoxos

---

### Post by majikstreet on 2006-02-04
[QUOTE=eudoxos]Hi everybody,

I have a breezy/dapper mix. Browsing (http) works just fine from firefox but if I do "[FONT="Fixedsys"]telnet [www.google.com](www.google.com) 80[/FONT]", it tries undefinitely.

This happens regardless of the service port: ssh is able to receive the remote machine fingerprint, but hangs after sending the password. Ssh worked under Windows, though (putty).

I have iptables flushed and ACCEPTing everything (FORWARD, INPUT, OUTPUT). I am completely clueless what is going on.

This machine is connected over WPA wireless to ADSL router, if that matters.

Thanks for any help,

Eudoxos[/QUOTE]

I've NEVER heard of using telnet to browse the web....

sudo apt-get install elinks

then elinks google.com

---

### Post by eudoxos on 2006-02-05
Thanks for the non-answer. I do NOT user telnet to browse. But telnet to the http port should yield the same results as browser does. The problem is that, as said, neither ssh works. And yes, it works from the same box from windows.  I wonder where's the blocker.

For those who may help, here are relevant tcpdumps:

```
mara@moira:~ > telnet www.google.com 80
Trying 64.233.183.103...

```
It does nothing (would timeout in a few minutes, ^-C).
```

root@moira:~ > tcpdump -vv port 80                                                                                         
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
10:12:58.748382 IP (tos 0x10, ttl  64, id 26395, offset 0, flags [DF], proto: TCP (6), length: 60) mygateway.ar7.38372 > www.google.com.www: S, cksum 0x6920 (correct), 2534037951:2534037951(0) win 5840 <mss 1460,sackOK,timestamp 2440868 0,nop,wscale 2>
10:13:01.748068 IP (tos 0x10, ttl  64, id 26396, offset 0, flags [DF], proto: TCP (6), length: 60) mygateway.ar7.38372 > www.google.com.www: S, cksum 0x5d67 (correct), 2534037951:2534037951(0) win 5840 <mss 1460,sackOK,timestamp 2443869 0,nop,wscale 2>
10:13:07.750432 IP (tos 0x10, ttl  64, id 26397, offset 0, flags [DF], proto: TCP (6), length: 60) mygateway.ar7.38372 > www.google.com.www: S, cksum 0x45f4 (correct), 2534037951:2534037951(0) win 5840 <mss 1460,sackOK,timestamp 2449872 0,nop,wscale 2>
10:13:19.768264 IP (tos 0x10, ttl  64, id 26398, offset 0, flags [DF], proto: TCP (6), length: 60) mygateway.ar7.38372 > www.google.com.www: S, cksum 0x1700 (correct), 2534037951:2534037951(0) win 5840 <mss 1460,sackOK,timestamp 2461892 0,nop,wscale 2>

4 packets captured
8 packets received by filter
0 packets dropped by kernel

```

Whereas when I try
```

mara@moira:~ > LC_ALL=C wget -N www.google.com                                                                               <
--10:14:52--  http://www.google.com/
           => `index.html'
Resolving www.google.com... 64.233.183.99
Connecting to www.google.com|64.233.183.99|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 0 [text/html]
Last-modified header missing -- time-stamps turned off.
--10:14:52--  http://www.google.com/
           => `index.html'
Reusing existing connection to www.google.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                                                                ] 2,452         --.--K/s

10:14:52 (87.04 KB/s) - `index.html' saved [2452]


```
and the dump is as follows:
```

root@moira:~ > tcpdump -vv port 80                                                                                           <
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
10:14:52.204131 IP (tos 0x0, ttl  64, id 7615, offset 0, flags [DF], proto: TCP (6), length: 60) mygateway.ar7.38373 > www.google.com.www: S, cksum 0x1c90 (correct), 2646336602:2646336602(0) win 5840 <mss 1460,sackOK,timestamp 2554341 0,nop,wscale 2>
10:14:52.234321 IP (tos 0x0, ttl 239, id 43693, offset 0, flags [none], proto: TCP (6), length: 44) www.google.com.www > mygateway.ar7.38373: S, cksum 0xb7f2 (correct), 3455965169:3455965169(0) ack 2646336603 win 8190 <mss 1360>
10:14:52.234365 IP (tos 0x0, ttl  64, id 7616, offset 0, flags [DF], proto: TCP (6), length: 40) mygateway.ar7.38373 > www.google.com.www: ., cksum 0xd879 (correct), 1:1(0) ack 1 win 5840
10:14:52.235229 IP (tos 0x0, ttl  64, id 7617, offset 0, flags [DF], proto: TCP (6), length: 141) mygateway.ar7.38373 > www.google.com.www: P 1:102(101) ack 1 win 5840
10:14:52.275128 IP (tos 0x0, ttl 239, id 10160, offset 0, flags [none], proto: TCP (6), length: 40) www.google.com.www > mygateway.ar7.38373: ., cksum 0xcf4b (correct), 1:1(0) ack 102 win 8089
10:14:52.276089 IP (tos 0x0, ttl  48, id 19242, offset 0, flags [none], proto: TCP (6), length: 40) www.google.com.www > mygateway.ar7.38373: ., cksum 0xd88c (correct), 1:1(0) ack 102 win 5720
10:14:52.282430 IP (tos 0x0, ttl  48, id 19243, offset 0, flags [none], proto: TCP (6), length: 357) www.google.com.www > mygateway.ar7.38373: P 1:318(317) ack 102 win 5720
10:14:52.282458 IP (tos 0x0, ttl  64, id 7618, offset 0, flags [DF], proto: TCP (6), length: 40) mygateway.ar7.38373 > www.google.com.www: ., cksum 0xd487 (correct), 102:102(0) ack 318 win 6432
10:14:52.306419 IP (tos 0x0, ttl  64, id 7619, offset 0, flags [DF], proto: TCP (6), length: 221) mygateway.ar7.38373 > www.google.com.www: P 102:283(181) ack 318 win 6432
10:14:52.357561 IP (tos 0x0, ttl  48, id 19244, offset 0, flags [none], proto: TCP (6), length: 1400) www.google.com.www > mygateway.ar7.38373: . 318:1678(1360) ack 283 win 6432
10:14:52.370572 IP (tos 0x0, ttl  48, id 19246, offset 0, flags [none], proto: TCP (6), length: 40) www.google.com.www > mygateway.ar7.38373: F, cksum 0xc9b0 (correct), 2911:2911(0) ack 283 win 6432
10:14:52.370596 IP (tos 0x0, ttl  64, id 7620, offset 0, flags [DF], proto: TCP (6), length: 40) mygateway.ar7.38373 > www.google.com.www: ., cksum 0xc272 (correct), 283:283(0) ack 1678 win 9520
10:14:52.382112 IP (tos 0x0, ttl  48, id 19245, offset 0, flags [none], proto: TCP (6), length: 1273) www.google.com.www > mygateway.ar7.38373: P 1678:2911(1233) ack 283 win 6432
10:14:52.382303 IP (tos 0x0, ttl  64, id 7621, offset 0, flags [DF], proto: TCP (6), length: 40) mygateway.ar7.38373 > www.google.com.www: ., cksum 0xb300 (correct), 283:283(0) ack 2912 win 12240
10:14:52.385583 IP (tos 0x0, ttl  64, id 7622, offset 0, flags [DF], proto: TCP (6), length: 40) mygateway.ar7.38373 > www.google.com.www: F, cksum 0xb2ff (correct), 283:283(0) ack 2912 win 12240
10:14:52.414244 IP (tos 0x0, ttl 239, id 0, offset 0, flags [DF], proto: TCP (6), length: 40) www.google.com.www > mygateway.ar7.38373: ., cksum 0xc9af (correct), 2912:2912(0) ack 284 win 6432

16 packets captured
32 packets received by filter
0 packets dropped by kernel

```

My box does not receive ACK from the remote server. Why?? Firewall off completely. Any clues?

---

### Post by eudoxos on 2006-02-07
Replying to myself: this seems to be an arcane low-level (sub-IP) networking issue. It has been reported many times (WRT ssh) and never answered. Posted details to [http://bugs.debian.org/296811](http://bugs.debian.org/296811) . Network gurus are kindly asked to help.

Eudoxos

---

### Post by Iowan on 2006-02-07
I'm probably COMPLETELY off base, but...
<>

never mind - I'll delete this when I figure out how...

---

