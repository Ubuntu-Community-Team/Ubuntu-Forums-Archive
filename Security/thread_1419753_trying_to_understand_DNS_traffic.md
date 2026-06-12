---
title: "trying to understand DNS traffic"
date: 2010-03-02
forum: Security
---

### Post by jacksmash on 2010-03-02
Hi, 

I'm collecting NetFlow traffic off of an ethernet tap at home (on my Ubuntu box). One thing I've noticed is a ton of DNS traffic. I'm wondering why this is? Is it because outside machines are constantly asking my router for DNS information? 

Here is a (portion of a) log that I pulled up just from today: 

```

            sIP|            dIP|sPort|dPort|pro|   packets|     bytes|      dur|
   A.B.C.D|    X.Y.0.94|63585|   53| 17|         1|        85|    0.035|
   A.B.C.D|    X.Y.0.95|63586|   53| 17|         1|        86|    0.034|
   A.B.C.D|    X.Y.0.94|63587|   53| 17|         1|        85|    0.031|
   A.B.C.D|    X.Y.0.95|63588|   53| 17|         1|        86|    0.029|
    X.Y.0.94|   A.B.C.D|   53|63585| 17|         1|        85|    0.000|
   A.B.C.D|    X.Y.0.94|63589|   53| 17|         1|        86|    0.030|
    X.Y.0.95|   A.B.C.D|   53|63586| 17|         1|        86|    0.000|
   A.B.C.D|    X.Y.0.95|63590|   53| 17|         1|        72|    0.028|
    X.Y.0.94|   A.B.C.D|   53|63587| 17|         1|        85|    0.000|
    X.Y.0.95|   A.B.C.D|   53|63588| 17|         1|        86|    0.000|
    X.Y.0.94|   A.B.C.D|   53|63589| 17|         1|        86|    0.000|
    X.Y.0.95|   A.B.C.D|   53|63590| 17|         1|        72|    0.000|
   A.B.C.D|    X.Y.0.94|63591|   53| 17|         2|       144|    0.028|
   A.B.C.D|    X.Y.0.95|63591|   53| 17|         1|        72|    0.017|
    X.Y.0.94|   A.B.C.D|   53|63591| 17|         2|       240|    0.011|
    X.Y.0.95|   A.B.C.D|   53|63591| 17|         1|       120|    0.000|
   A.B.C.D|    X.Y.0.95|63592|   53| 17|         1|        73|    0.022|
   A.B.C.D|    X.Y.0.94|63593|   53| 17|         1|        72|    0.025|
   A.B.C.D|    X.Y.0.95|63594|   53| 17|         1|        73|    0.028|
    X.Y.0.95|   A.B.C.D|   53|63592| 17|         1|       121|    0.000|
   A.B.C.D|    X.Y.0.94|63595|   53| 17|         1|        73|    0.029|
    X.Y.0.94|   A.B.C.D|   53|63593| 17|         1|       120|    0.000|
    X.Y.0.95|   A.B.C.D|   53|63594| 17|         1|       121|    0.000|
    X.Y.0.94|   A.B.C.D|   53|63595| 17|         1|       121|    0.000|
   A.B.C.D|    X.Y.0.95|63596|   53| 17|         1|        73|    0.012|
    X.Y.0.95|   A.B.C.D|   53|63596| 17|         1|       118|    0.000|
   A.B.C.D|    X.Y.0.94|63597|   53| 17|         1|        59|    0.011|
    X.Y.0.94|   A.B.C.D|   53|63597| 17|         1|       174|    0.000|
   A.B.C.D|    X.Y.0.95|63598|   53| 17|         1|        61|    0.030|
   A.B.C.D|    X.Y.0.94|63599|   53| 17|         1|        74|    0.033|
   A.B.C.D|    X.Y.0.94|63601|   53| 17|         1|        77|    0.028|
   A.B.C.D|    X.Y.0.95|63600|   53| 17|         1|        75|    0.028|
    X.Y.0.95|   A.B.C.D|   53|63598| 17|         1|       152|    0.000|
   A.B.C.D|    X.Y.0.95|63602|   53| 17|         1|        62|    0.026|
    X.Y.0.94|   A.B.C.D|   53|63599| 17|         1|       168|    0.000|
    X.Y.0.95|   A.B.C.D|   53|63600| 17|         1|       126|    0.000|
    X.Y.0.94|   A.B.C.D|   53|63601| 17|         1|       197|    0.000|
   A.B.C.D|    X.Y.0.94|63603|   53| 17|         1|        60|    0.027|
    X.Y.0.95|   A.B.C.D|   53|63602| 17|         1|       114|    0.000|
    X.Y.0.94|   A.B.C.D|   53|63603| 17|         1|       176|    0.000|

```

Note that A.B.C.D is my gateway address.

Any insights would be appreciated. Thanks!

---

### Post by jacksmash on 2010-03-02
By using dig on the 2 outside hosts, I realize that they are the DNS servers for my ISP. So, I guess my question is still "why so much traffic?" Also, a lot of this traffic gets flagged by Snort as an alert because it thinks there are attempted DNS spoof attacks.

---

### Post by Kinstonian on 2010-03-02
DNS is a common protocol.  However, to answer your question better, you need more details on the DNS traffic.  I suggest you run Wireshark with a DNS filter so you can see the actual DNS requests, which should shed some light on exactly what is going on.

---

### Post by jacksmash on 2010-03-02
Ok, I've logged in remotely to my machine, so I can't use wireshark right now, but I did use tcpdump:

```

13:56:35.566048 IP (tos 0x0, ttl 63, id 36267, offset 0, flags [DF], proto UDP (17), length 73)
    A.B.C.D.60959 > X.Y.0.95.53: [udp sum ok] 64585+ PTR? E.F.G.H.in-addr.arpa. (45)
13:56:35.592802 IP (tos 0x60, ttl 249, id 11481, offset 0, flags [DF], proto UDP (17), length 115)
    X.Y.0.95.53 > A.B.C.D.60959: [udp sum ok] 64585 q: PTR? E.F.G.H.in-addr.arpa. 1/0/0 E.F.G.H.in-addr.arpa. [58m48s] PTR Dynamic****.some.domain.com. (87)

```

Ok, so this is captured when I ssh'd into my machine. "A.B.C.D" is the IP of the host I'm logging on to. "X.Y.0.95" is the dns server for my ISP. "E.F.G.H" is the host I'm currently on.

So, it looks like my remote machine makes a DNS request whenever I log in remotely. This is fine.

But sometimes Snort logs this type of DNS communication:

```

DNS SPOOF query response with TTL of 1 min. and no authority

```

And when I dig deeper into the logs, I can see that I was talking to a familiar website (e.g., sans.org, or a news website like ctv.ca, etc.). So I'm looking to understand what is happening that it causing the alert.

Will Wireshark tell me more than tcpdump and Snort logs? Again, I can't use Wireshark since I've logged in remotely.

Thanks!

---

### Post by The Cog on 2010-03-02
You can use wireshark remotely. You ssh in with the -X option for X tunneling (also perhaps -C for compression) and launch wireshark with gksu wireshark. Make sure your capture filter omits the SSH session traffic or you'll just swamp with an infinite loop of reporting its own reporting its own reporting its own...

---

### Post by noway2 on 2010-03-02
A dns query when you log in is normal.  Also, whenever you visit a webpage a lookup will be done.  Do you see any address look ups for sights you don't recognize?

---

### Post by OpSecShellshock on 2010-03-02
You can also go out to snortid.com and put 1:254 into the search box. Those descriptions might not tell you much, but it's a start. I'm inclined to believe it's a false positive. I think this one fires because instead of querying an authoritative dns server, your computer is querying your ISP's servers and getting cached information (they do this to make web use faster). As long as the source IP in the Snort log is X.Y.0.95 and the destination IP is A.B.C.D then you're probably fine.

---

### Post by jacksmash on 2010-03-03
Ok, so what I did is checked all the flow data, ignoring any DNS traffic to/from my ISP's DNS servers.

Here was the result:

```

            sIP|            dIP|sPort|dPort|pro|   packets|     bytes|   flags|      dur|
218.244.231.132|   A.B.C.D| 6000|   53|  6|         1|        40| S      |    0.000|
    71.62.12.29|   A.B.C.D|   53|43802| 17|         1|       134|        |    0.000|
218.244.231.132|   A.B.C.D| 6000|   53|  6|         1|        40| S      |    0.000|
 173.213.98.209|   A.B.C.D|   53| 1024|  6|         1|        40|  R A   |    0.000|
222.133.182.194|   A.B.C.D| 6000|   53|  6|         1|        40| S      |    0.000|
218.244.231.132|   A.B.C.D| 6000|   53|  6|         1|        40| S      |    0.000|
    218.4.58.82|   A.B.C.D| 6000|   53|  6|         1|        40| S      |    0.000|
208.115.208.199|   A.B.C.D|   53|43802| 17|         1|       126|        |    0.000|
222.133.182.194|   A.B.C.D| 6000|   53|  6|         1|        40| S      |    0.000|
    218.4.58.82|   A.B.C.D| 6000|   53|  6|         1|        40| S      |    0.000|
222.133.182.194|   A.B.C.D| 6000|   53|  6|         1|        40| S      |    0.000|

```

There's as IP from China in there (218.4.58.82), but I find it interesting that this is mostly TCP traffic. That Chinese host does not show up in my Snort logs, and I'm wondering if that's just because the TCP protocol is being abused in some way. Note that for the TCP traffic (pro=6) that sPort 6000 is being used.

Note also dPort 43802. I find that attempts to this port are often made from BitTorrent clients. But why the sPort in this case is 53 is beyond me.

Interesting.

---

### Post by Kinstonian on 2010-03-03
You're not the only person getting traffic with a source port of 6000 from different IPs.  I believe it generally comes from China.  Check out [SANS ISC](http://isc.sans.org/diary.html?date=2010-01-09) for more information.  The [Dasher worm](http://vil.nai.com/vil/content/v_137567.htm\) also uses a source port of 6000 and apparently also uses TCP port 53 like what you're seeing.

For the UDP dst port of 43802, you can see those packets contain application data, so again you need to use tcpdump/wireshark for more details.  Session data is great for traffic analysis, but you will eventually want more details.

---

### Post by jacksmash on 2010-03-04
Ok, thanks for everyone's help with this! I think I'm getting somewhere with my understanding...

I've installed Wireshark on my collection machine and am using x-forwarding.

I thought the first thing I would do is look at the DNS traffic which is causing Snort alerts.

Recall: here is the alert:

```
DNS SPOOF query response with TTL of 1 min. and no authority
```

The address being queried is: [www.sans.org](www.sans.org).

In the response, one of the flags states: "Authoritative: Server is not an authority for domain". But I see that on all of the DNS responses I've looked at, so I can't imagine that is what's causing the Snort alert.

Also, the TTL under the "Internet Protocol" section is 249, so that also doesn't seem to correspond with the Snort alert.

So... what else should I be looking at with Wireshark to see what is causing the Snort alert?

Cheers.

---

### Post by Kinstonian on 2010-03-04
It's not the IP TTL, it's the DNS TTL that is set to 1 minute, which means the DNS answer should be cached for 1 minute.

---

### Post by jacksmash on 2010-03-05
Ok, so why is it only caching the DNS response for a minute? It seems that the response is valid, i.e., it's providing the correct IP address...

---

### Post by Kinstonian on 2010-03-06
> **jacksmash said:**
> Ok, so why is it only caching the DNS response for a minute? It seems that the response is valid, i.e., it's providing the correct IP address...

This [blog post](http://taosecurity.blogspot.com/2003/12/understanding-snort-dns-ttl-alerts.html) explains it pretty well.

---

