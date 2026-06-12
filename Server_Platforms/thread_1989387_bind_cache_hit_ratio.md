---
title: "bind cache hit ratio"
date: 2012-05-28
forum: Server Platforms
---

### Post by MG2R on 2012-05-28
As a means of learning something about the internet's inner workings (and to not get bored), I set up a DNS cache on my home server. It's working and logging perfectly at the moment.

I wanted to know if there is a way reading the "cache hit ratio" (e.g.: how many of my queries were in the cache divided by the total amount of queries)

---

### Post by Doug S on 2012-05-29
I am not aware of such a query command, but would also be interested.
 
What I have done in the past is run tcpdump monitoring port 53 on both the local nic and the external nic, then compared the results to get a rough idea of hit ratio and amount of external traffic saved.

---

### Post by MG2R on 2012-05-29
> **Doug S said:**
> 
What I have done in the past is run tcpdump monitoring port 53 on both the local nic and the external nic, then compared the results to get a rough idea of hit ratio and amount of external traffic saved.

Oh, that's very clever. The problem I have is that I use only one nic (eth0), my server is not my gateway.

---

### Post by Doug S on 2012-05-30
In that case I think you could monitor your loopback interface. For example```
doug@doug-64:~$ sudo tcpdump -i lo -n -nn -tttt port 53
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on lo, link-type EN10MB (Ethernet), capture size 65535 bytes
2012-05-29 23:41:26.558072 IP 127.0.0.1.47143 > 127.0.0.1.53: 26517+ PTR? 100.111.168.192.in-addr.arpa. (46)
2012-05-29 23:41:26.558246 IP 127.0.0.1.53 > 127.0.0.1.47143: 26517* 1/1/1 PTR doug-xps.smythies.com. (115)
2012-05-29 23:41:26.558467 IP 127.0.0.1.43061 > 127.0.0.1.53: 37506+ A? doug-xps.smythies.com. (39)
2012-05-29 23:41:26.558577 IP 127.0.0.1.53 > 127.0.0.1.43061: 37506* 1/1/1 A 192.168.111.100 (89)
2012-05-29 23:43:36.582274 IP 127.0.0.1.56181 > 127.0.0.1.53: 42996+ A? cnn.com. (25)
2012-05-29 23:43:36.613063 IP 127.0.0.1.53 > 127.0.0.1.56181: 42996 4/13/0 A 157.166.255.18, A 157.166.255.19, A 157.166.226.25, A 157.166.226.26 (300)
```

---

### Post by robgr85 on 2012-05-30
Have You tried to analyze analyze bind9 built in statistics functionality?

---

