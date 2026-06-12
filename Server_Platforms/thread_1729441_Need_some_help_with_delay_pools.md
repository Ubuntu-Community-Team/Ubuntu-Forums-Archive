---
title: "Need some help with delay pools"
date: 2011-04-14
forum: Server Platforms
---

### Post by b3rkl3y on 2011-04-14
Hello there, 

I'm trying to get delay pools working on my squid, but I'm getting some unexpected results.

My main objectives are:

* allow only 128kbps for each user on network A
* allow only 256kbps for each user on network B
* unlimited traffic for adminip

Looks like that all my users together on network A cant get more than 128kbps, the delay pools are working only for the entire subnet and not for each host.

Same thing happens to network B (256kbps instead).

I just want to avoid a few users making the internet slow for everyone else.

Here's my delay pools config:

```

acl 128kbps src 172.18.0.0/24
acl 256kbps src 172.16.0.0/24
acl adminip src 172.18.0.221/32

delay_pools 3

delay_class 1 2
delay_access 1 deny adminip
delay_access 1 deny 256kbps
delay_access 1 allow 128kbps
delay_parameters 1 -1/-1 16000/16000

delay_class 2 2
delay_access 2 deny adminip
delay_access 2 allow 256kbps
delay_parameters 2 -1/-1 32000/32000

delay_class 3 2
delay_access 3 allow adminip
delay_parameters 3 -1/-1 -1/-1

```


Thank you for your attention.

---

