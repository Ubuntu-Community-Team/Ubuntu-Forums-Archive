---
title: "TCP Fast Open - recent increase in activity"
date: 2022-08-11
forum: Security
---

### Post by Doug S on 2022-08-11
Hi All,

I have noticed a sudden and sustained increase in TCP SYN packets specifying the "Fast Open" option (34) to my WAN facing server for port 80. The attached graph shows such packets per hour since September, mostly none until a couple of weeks ago. This week alone there have been such packets from 489 different IP addresses.

My server used to respond, and by the default settings would ACK 5 times before giving up. The TCP open sequence never completed thereafter, and my connection tracking table would sit in the "SYN_RECV" state for the 60 seconds timeout period. Now I have added these rules to my iptables rule set:

```

# Ver: 3.18: Deal with TFO (TCP Fast Open). Comment / Uncomment logging line as desired.
# TFO is Option 34.
$IPTABLES -A INPUT -i $EXTIF -p tcp -m state --state NEW --tcp-option 34 -j LOG --log-prefix "TFO:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -p tcp -m state --state NEW --tcp-option 34 -j DROP

```
That rule has been hit 22,500 times since I added a test version, on the fly, about a week ago.

As is often the case, I don't understand the point here. Perhaps there is some vulnerability with some web servers that accept fast open, or perhaps the source IP address is spoofed and they are merely trying to obtain a 5 to 1 gain on spam packets.
Just wondering if others have seen this one, as it seems new to me?

Example tcpdump captures:

```

2022-08-10 12:59:05.863151 IP 20.187.115.233.180 > AAA.BBB.CCC.DDD.80: Flags [S], seq 3951787430, win 64240, options [mss 1353,sackOK,TS val 2044291235 ecr 0,nop,wscale 7,[COLOR="#FF0000"]tfo  (invalid)[/COLOR]], length 0
2022-08-10 12:59:19.397893 IP 20.239.77.227.24434 > AAA.BBB.CCC.DDD.80: Flags [S], seq 2148153193, win 65535, options [mss 1283,sackOK,TS val 2178508963 ecr 0,nop,wscale 6,[COLOR="#FF0000"]tfo  (invalid)[/COLOR]], length 0
2022-08-10 12:59:22.191508 IP 52.140.217.194.44385 > AAA.BBB.CCC.DDD.80: Flags [S], seq 2171335198, win 64240, options [mss 1305,sackOK,TS val 165243043 ecr 0,nop,wscale 6,[COLOR="#FF0000"]tfo  (invalid)[/COLOR]], length 0
2022-08-10 12:59:23.807251 IP 104.208.77.116.38455 > AAA.BBB.CCC.DDD.80: Flags [S], seq 1428782077, win 64240, options [mss 1293,sackOK,TS val 1373202595 ecr 0,nop,wscale 8,[COLOR="#FF0000"]tfo  (invalid)[/COLOR]], length 0
2022-08-10 13:01:01.506653 IP 93.157.63.41.65000 > AAA.BBB.CCC.DDD.80: Flags [S], seq 2065309080, win 29200, options [mss 1387,sackOK,TS val 735668387 ecr 0,nop,wscale 9,[COLOR="#FF0000"]tfo  (invalid)[/COLOR]], length 0
2022-08-10 13:01:01.779188 IP 103.157.27.220.4641 > AAA.BBB.CCC.DDD.80: Flags [S], seq 2672671499, win 64240, options [mss 1374,sackOK,TS val 2027514019 ecr 0,nop,wscale 7,[COLOR="#FF0000"]tfo  (invalid)[/COLOR]], length 0
2022-08-10 13:03:35.408631 IP 93.157.63.41.53971 > AAA.BBB.CCC.DDD.80: Flags [S], seq 3523017278, win 65535, options [mss 1398,sackOK,TS val 2665048227 ecr 0,nop,wscale 9,[COLOR="#FF0000"]tfo  (invalid)[/COLOR]], length 0
2022-08-10 13:03:35.873037 IP 103.157.27.220.56191 > AAA.BBB.CCC.DDD.80: Flags [S], seq 1406806619, win 64240, options [mss 1269,sackOK,TS val 4158220451 ecr 0,nop,wscale 9,[COLOR="#FF0000"]tfo  (invalid)[/COLOR]], length 0

```

EDIT: [Possibly related article]("https://isc.sans.edu/diary/Odd+TCP+Fast+Open+Packets.+Anybody+understands+why%3F/28766") (I signed up for an account and tried to add a comment, but couldn't figure out how to). [And another]("https://www.cisco.com/c/en/us/support/docs/csa/cisco-sa-snort-tfo-bypass-MmzZrtes.html"). [A 3rd]("https://www.cvedetails.com/cve/CVE-2015-3332/").

EDIT 2: The only non invalid TCP SYN with TFO packets my server got were:

```

2021-12-14 07:57:11.020868 IP 64.179.169.12.42150 > AAA.BBB.CCC.DDD.80: Flags [S], seq 346959514, win 64240, options [mss 1460,nop,nop,sackOK,nop,wscale 7,tfo  cookiereq,nop,nop], length 0
2021-12-14 07:57:48.918140 IP 64.179.169.12.46258 > AAA.BBB.CCC.DDD.443: Flags [S], seq 2775176416, win 64240, options [mss 1460,nop,nop,sackOK,nop,wscale 7,tfo  cookiereq,nop,nop], length 0
2021-12-14 07:58:07.937147 IP 64.179.169.12.46952 > AAA.BBB.CCC.DDD.443: Flags [S], seq 723079057, win 64240, options [mss 1460,nop,nop,sackOK,nop,wscale 7,tfo  cookiereq,nop,nop], length 0
2021-12-31 23:25:31.639870 IP 64.179.169.12.35498 > AAA.BBB.CCC.DDD.80: Flags [S], seq 2467483105, win 64240, options [mss 1460,nop,nop,sackOK,nop,wscale 7,tfo  cookiereq,nop,nop], length 0
2021-12-31 23:26:00.698648 IP 64.179.169.12.40298 > AAA.BBB.CCC.DDD.443: Flags [S], seq 74209052, win 64240, options [mss 1460,nop,nop,sackOK,nop,wscale 7,tfo  cookiereq,nop,nop], length 0
2021-12-31 23:26:14.887047 IP 64.179.169.12.40946 > AAA.BBB.CCC.DDD.443: Flags [S], seq 2579710369, win 64240, options [mss 1460,nop,nop,sackOK,nop,wscale 7,tfo  cookiereq,nop,nop], length 0
2022-01-13 00:13:05.436201 IP 64.179.169.12.50096 > AAA.BBB.CCC.DDD.80: Flags [S], seq 3230468183, win 64240, options [mss 1460,nop,nop,sackOK,nop,wscale 7,tfo  cookiereq,nop,nop], length 0
2022-01-13 00:13:36.111147 IP 64.179.169.12.55166 > AAA.BBB.CCC.DDD.443: Flags [S], seq 1826579325, win 64240, options [mss 1460,nop,nop,sackOK,nop,wscale 7,tfo  cookiereq,nop,nop], length 0
2022-01-13 00:13:56.596996 IP 64.179.169.12.56154 > AAA.BBB.CCC.DDD.443: Flags [S], seq 2412386176, win 64240, options [mss 1460,nop,nop,sackOK,nop,wscale 7,tfo  cookiereq,nop,nop], length 0

```And while the open sequences were completed (the normal way, not the TFO way) and an actual GET issued, 64.179.169.12 seemed to have been up to no good, and so I don't have a concern with now just DROPping such packets.

---

### Post by TheFu on 2022-08-11
[https://www.iana.org/assignments/tcp-parameters/tcp-parameters.xhtml](https://www.iana.org/assignments/tcp-parameters/tcp-parameters.xhtml)

Says that people are using it, but it isn't approved in the standard.  I'd drop all those packets, but it appears Linux systems running some 3.x series kernels are the only ones impacted.

Ubuntu 18.04 and later supports HWE kernels 5.4.x, so we aren't impacted.  If I used a linux based router (like I suspect most of the home users do), I'd want to check the kernel version used.  Fortunately, my WAN router runs pf and BSD, which is well maintained and has nearly weekly patches for security issues.

---

### Post by #&amp;thj^% on 2022-08-11
Doug S I wonder if these are related to Blackhole-ing?
And this setting:
34 	variable 	TCP Fast Open Cookie 	[RFC7413] :[https://www.rfc-editor.org/rfc/rfc7413.html](https://www.rfc-editor.org/rfc/rfc7413.html)


I set mine as:
```
net.ipv4.tcp_fastopen_blackhole_timeout_sec sysctl to 0
```
[list]
[https://www.iana.org/assignments/tcp-parameters/tcp-parameters.xhtml#tcp-parameters-1](https://www.iana.org/assignments/tcp-parameters/tcp-parameters.xhtml#tcp-parameters-1)
While TFO is a neat mechanism to reduce TCP overhead, implementing it properly is harder than it should be. Even if almost all the work is already done in the kernel, TFO implementation is challenging due to:
IE:
```
netstat -nat -s | grep TCPF

```


    [*]Lack of documentation on counters and how to interpret them
    [*]Lack of documentation on the socket options involved
   [*] Sysctl defaults that do not allow passive TFO
    [*]An extremely aggressive black holing mechanism[/list]

TFO may be fast but adoption is slow. To increase TFO adoption these issues need to be addressed.
```
netstat -nat -s | grep TCP
    271 TCP sockets finished time wait in fast timer
    TCPSackRecovery: 337
    TCPDSACKUndo: 8
    TCPLostRetransmit: 3294
    TCPTimeouts: 4580
    TCPLossProbes: 264
    TCPLossProbeRecovery: 11
    TCPSackRecoveryFail: 16
    TCPBacklogCoalesce: 2680
    TCPDSACKOldSent: 806
    TCPDSACKOfoSent: 40
    TCPDSACKRecv: 31
    TCPDSACKIgnoredNoUndo: 14
    TCPSackShifted: 101
    TCPSackMerged: 646
    TCPSackShiftFallback: 448
    TCPRetransFail: 76
    TCPRcvCoalesce: 239450
    TCPOFOQueue: 130707
    TCPOFOMerge: 38
    TCPChallengeACK: 17
    TCPSYNChallenge: 18
    TCPAutoCorking: 1191
    TCPSynRetrans: 4475
    TCPOrigDataSent: 30073
    TCPHystartTrainDetect: 4
    TCPHystartTrainCwnd: 75
    TCPACKSkippedChallenge: 1
    TCPWinProbe: 8
    TCPKeepAlive: 291
    TCPDelivered: 30334
    TCPAckCompressed: 83870
    TCPDSACKRecvSegs: 31


```
and:
```
nstat –az
#kernel

```

---

### Post by Doug S on 2022-08-13
> **1fallen said:**
> Doug S I wonder if these are related to Blackhole-ing?
And this setting:
34 	variable 	TCP Fast Open Cookie 	[RFC7413] :[https://www.rfc-editor.org/rfc/rfc7413.html](https://www.rfc-editor.org/rfc/rfc7413.html)

Hi TheFu and 1fallen, and thank you for chiming in.

I don't know if it is related to Blackhol-ing or what. The related issues we have discussed or referenced are not new so I am wondering why the sudden increase in activity? I have observed similar things over the years, where some new probe pattern seems to become all the rage, yet I can not figure out what they are attempting to do. My server never was under any threat, but at least now it is not replying with a SYN ACK 5 times per SYN packet.

---

### Post by TheFu on 2022-08-13
> **Doug S said:**
> Hi TheFu and 1fallen, and thank you for chiming in.

I don't know if it is related to Blackhol-ing or what. The related issues we have discussed or referenced are not new so I am wondering why the sudden increase in activity? I have observed similar things over the years, where some new probe pattern seems to become all the rage, yet I can not figure out what they are attempting to do. My server never was under any threat, but at least now it is not replying with a SYN ACK 5 times per SYN packet.

Could they be looking for older, CentOS systems?  Lots of people put internet systems up and never do any more support until their systems stop working. 

A good friend used to work at a small hosting provider and he has stories of systems that hadn't been patched in 5 yrs, but as long as the webpage seemed to be working, it didn't matter how much spam or other crap the systems were doing as far as the client was concerned.  Don't touch what is still working, who cares about security or that others were using their systems to attack the world?  That company had a policy - don't touch client systems, until they asked, then upsell them to a fully-maintained, support contract for $100s/month, fix the issues about a week later, so they felt the pain, and were happy to pay for the support, then leave it alone for a year and do yearly updates along with daily backups.  Most of this little websites were poorly written php code that the little company (domain owners) had paid $500 to some college kid to create and they didn't want to spend $10,000 to have a proper, secure, webapp.  Spending $200/month for a server that is making $5000/month was a good trade the way they saw it.  When it becomes too much hassle, fix it 1 more time, then "sell" the business to someone else. Most of these little companies had 1 server per product they sold and kept each as a different business. They'd tried 50-100 little 1-product businesses like this, but only had 5-10 that were profitable. That was sufficient for a single family to live off.

---

### Post by #&amp;thj^% on 2022-08-13
+1 To TheFu's statement, this time of year most always brings out spammers, sniffers, script kiddies, and just bad actors.
Your reported numbers are small in comparison to what I see at work. Over 150,000 per minute. and growing.
Now you know how I lost my mind. :D

---

### Post by Doug S on 2022-08-16
> **TheFu said:**
> Could they be looking for older, CentOS systems? I suppose. I do somewhat drive myself crazy trying to understand why and why on and on and on with these things.

> **1fallen said:**
> +1 To TheFu's statement, this time of year most always brings out spammers, sniffers, script kiddies, and just bad actors.I haven't noticed any particular time of year for increased activity before. I have noticed more of a general decrease in hacker activity about 20 to 15 years ago, and then a constant increase in the last decade.

Anyway, this particular one, TFO (TCP Fast Open), seems to be winding down against my external IP address in the last couple of days. Only 41 packets in the last 4 hours, and sometimes 0 packets per hour.

---

### Post by Doug S on 2022-08-27
There are a couple of [ articles]("https://www.bleepingcomputer.com/news/security/cisa-is-warning-of-high-severity-pan-os-ddos-flaw-used-in-attacks/") about TCP fast open being used in a DDoS attack. and [this one]("https://security.paloaltonetworks.com/CVE-2022-0028")

EDIT: This event ended Aug 27 08:56:11PDT after involving 1769 different source IPs, 63,864 packets, and this recent burst of activity spanning 1000 hours.

---

### Post by #&amp;thj^% on 2022-09-08
> **Doug S said:**
> There are a couple of [ articles]("https://www.bleepingcomputer.com/news/security/cisa-is-warning-of-high-severity-pan-os-ddos-flaw-used-in-attacks/") about TCP fast open being used in a DDoS attack. and [this one]("https://security.paloaltonetworks.com/CVE-2022-0028")

EDIT: This event ended Aug 27 08:56:11PDT after involving 1769 different source IPs, 63,864 packets, and this recent burst of activity spanning 1000 hours.

Sorry for a late reply, but thanks Doug S for the links, good reads.

---

### Post by Doug S on 2023-01-23
After months of no TFO packets at all, there were 26  between Jan 15-18 from 5 different IP addresses from 5 different countries, but quiet since.

---

