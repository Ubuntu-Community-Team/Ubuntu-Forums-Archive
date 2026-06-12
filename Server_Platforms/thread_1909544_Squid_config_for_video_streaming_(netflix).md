---
title: "Squid config for video streaming (netflix)"
date: 2012-01-15
forum: Server Platforms
---

### Post by oldskool on 2012-01-15
I feel a bit ashamed asking this as i should know this. 

Background is, i have a Ubuntu server based in the U.S.A (i'm in the UK). I installed Squid on it to help me do some research on google adwords U.S.A... as direct it would geo-target me. 

Anyway, i realised that the proxy is also useful to allow me to watch netflix in the USA which has more content. 

I understand that all traffic (data) goes through the proxy which means if i'm watching netflix its technically going through the proxy, meaning eating gigs of data on my server hosting package... is this assumption correct? 

Is there any possible way to configure the proxy to be anonymous (already done) but also ensure the connection goes direct to the user IP so it doesn't use my server hosting data/bandwidth? 

Thanks

---

### Post by CharlesA on 2012-01-15
That's correct. If you are using it as a Proxy, then all data is being send thru the server.

I don't think it's possible to forward the traffic as you want, it would have to go thru the proxy before being sent to another machine.

---

