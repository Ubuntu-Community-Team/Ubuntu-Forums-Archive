---
title: "Squid Proxy"
date: 2011-05-03
forum: Server Platforms
---

### Post by Vaxon on 2011-05-03
Hello I currently run ubuntu server 10.04 in a virtualbox
and it runs wonderfully

I would like to install squid as a proxy server
But from the research I've done on it, it only handles jobs from your local network

I would like to set it up so that say I'm at a friends house, or a public library
I could use my squid server as a proxy to allow me to sites that may be blocked

---

### Post by hawk2010 on 2011-05-04
Vaxon, i think it will be highly unlikely you can achive this as those places may not allow outbound port 3128 connectivity to public IPs. I think the way should be that your squid to run on port 80. but this is just experimental. But before that you need to do the following

1. Static broadband IP or have dyndns
2. configure squid to use port 80
3. port forward your router to forward all requests coming from outside to ur squid
4. define the ACLs so that you include ur school or friend's home IPs
5. I recommend you use squid authentication as you wouldn't won't bad guys visiting sites and committing crime using your open proxy!


> **Vaxon said:**
> Hello I currently run ubuntu server 10.04 in a virtualbox
and it runs wonderfully

I would like to install squid as a proxy server
But from the research I've done on it, it only handles jobs from your local network

I would like to set it up so that say I'm at a friends house, or a public library
I could use my squid server as a proxy to allow me to sites that may be blocked

---

### Post by i.r.id10t on 2011-05-04
Have squid listen on the default port, set up a ssh server, ssh into your private network w/ some port forwarding to use the proxy.

---

