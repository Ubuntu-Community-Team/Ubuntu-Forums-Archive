---
title: "Some sites blocked"
date: 2011-02-09
forum: Security
---

### Post by crocos on 2011-02-09
Hello,

In the past week or so I've noticed some weird network behaviour. I find accessing some sites such as Amazon, Paypal, and Bigstockphoto really slow. Sometimes the page will not load at all. Other sites are fine. The problem sites are not a problem for others on my LAN at home. When I try to open the problem sites, I can see in Firestarter blocked connections coming from 2.1(8/9).xxx.xxx on various ports such as 36007. This only happens for the problem sites. Apologies in advance if I'm missing something obvious. I attached a typical output from firestarter.

Cheers,

Neil

PS. This happens with Firfeox or Chrome.
Using Ubuntu 10.10

---

### Post by cariboo on 2011-02-09
What service is connecting to Akamai Technologies? Use :

```
lsof -i -P
```

to find out.

---

### Post by crocos on 2011-02-09
> **cariboo907 said:**
> What service is connecting to Akamai Technologies? Use :

```
lsof -i -P
```

to find out.
Thanks for the reply.


gvfsd-htt 13055   24u  IPv4  971318      0t0  TCP Q330:52240->a88-221-94-210.deploy.akamaitechnologies.com:80 (CLOSE_WAIT)

npviewer. 26176    12u  IPv4 1033839      0t0  TCP Q330:53641->a88-221-94-150.deploy.akamaitechnologies.com:1935 (ESTABLISHED)

and


clock-app  2786 neil   23u  IPv4 1046212      0t0  TCP Q330:43806->a88-221-94-234.deploy.akamaitechnologies.com:80 (CLOSE_WAIT)

---

### Post by crocos on 2011-02-09
I killed those processes that were connecting to Akamai tech. And tried to connect to Amazon.co.uk again. Still can't access, and Amazon tries to connect to me using odd ports:

Time:Feb 10 00:08:58 Direction: Unknown In:eth1 Out: Port:44147 Source:178.236.6.39 Destination:192.168.1.82 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Feb 10 00:08:58 Direction: Unknown In:eth1 Out: Port:44148 Source:178.236.6.39 Destination:192.168.1.82 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Feb 10 00:09:22 Direction: Unknown In:eth1 Out: Port:44147 Source:178.236.6.39 Destination:192.168.1.82 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Feb 10 00:09:22 Direction: Unknown In:eth1 Out: Port:44148 Source:178.236.6.39 Destination:192.168.1.82 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Feb 10 00:09:30 Direction: Unknown In:eth1 Out: Port:44132 Source:178.236.6.39 Destination:192.168.1.82 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Feb 10 00:09:30 Direction: Unknown In:eth1 Out: Port:44133 Source:178.236.6.39 Destination:192.168.1.82 Length:44 TOS:0x00 Protocol:TCP Service:Unknown

---

### Post by wacky_sung on 2011-02-11
> **crocos said:**
> I killed those processes that were connecting to Akamai tech. And tried to connect to Amazon.co.uk again. Still can't access, and Amazon tries to connect to me using odd ports:

Time:Feb 10 00:08:58 Direction: Unknown In:eth1 Out: Port:44147 Source:178.236.6.39 Destination:192.168.1.82 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Feb 10 00:08:58 Direction: Unknown In:eth1 Out: Port:44148 Source:178.236.6.39 Destination:192.168.1.82 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Feb 10 00:09:22 Direction: Unknown In:eth1 Out: Port:44147 Source:178.236.6.39 Destination:192.168.1.82 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Feb 10 00:09:22 Direction: Unknown In:eth1 Out: Port:44148 Source:178.236.6.39 Destination:192.168.1.82 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Feb 10 00:09:30 Direction: Unknown In:eth1 Out: Port:44132 Source:178.236.6.39 Destination:192.168.1.82 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Feb 10 00:09:30 Direction: Unknown In:eth1 Out: Port:44133 Source:178.236.6.39 Destination:192.168.1.82 Length:44 TOS:0x00 Protocol:TCP Service:Unknown

I do not what went wrong on your system but all the mention sites went smooth for me. Just to update you that those sites has been under heavy DDOS attack lately but not sure how long does it gonna last.

---

