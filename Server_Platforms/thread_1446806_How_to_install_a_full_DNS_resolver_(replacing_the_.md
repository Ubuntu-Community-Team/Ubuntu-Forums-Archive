---
title: "How to install a full DNS resolver (replacing the stub resolver)"
date: 2010-04-04
forum: Server Platforms
---

### Post by arjun.prakash on 2010-04-04
Hi,
I have a DNS Server which cannot process Recursive DNS queries. My ubuntu system is not able to work with this DNS server as the glibc resolver cannot do Iterative queries (i.e. It is not processing the referrals sent by the DNS server). I read in a few posts that linux and windows resolvers are usually stub-resolvers which can only do Recursive queries. 
Is there any way to install a DNS client in ubuntu which can do Iterative queries? 
I guess installing BIND and configuring it would help; but I am looking for just the DNS client (w/o server) to do the job.
Thanks..

---

### Post by mbehamin on 2010-04-06
Hi 
as i know the client naming service does not support iteration and the only way is that having cache-only name server on your linux client .  :(


regards

---

### Post by romeroc24 on 2010-04-06
Bind can do recursive queries, like a client asking other servers on internet, look at the my server's asking (192.168.1.254 port 16599) to other external server (209.6.3.210 port 53) and the response below.

```
$ sudo tcpdump -n
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
20:19:21.732149 **IP 192.168.1.254.16599 > 209.6.3.210.53: 3457 [1au] A? ubuntuforums.org. (45)**
20:19:22.097599 **IP 209.6.3.210.53 > 192.168.1.254.16599: 3457*- 1/3/4 A[|domain]**

```

Recursive queries are default in bind.

---

