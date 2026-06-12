---
title: "Quick way to balance backend servers"
date: 2010-05-27
forum: Server Platforms
---

### Post by jmazaredo on 2010-05-27
Hi,

Currently having trouble balancing https request going to my backend servers.

Basically I have a balancer project server with two identical backend server serving https request.

Tried nginx, perlbal but all i can balance is the http. 

All i want to do is the balancer will just route and balance the http and https request. The one who should issue certificate is the backend servers.

---

### Post by craigp84 on 2010-05-29
I think you're muddling yourself up here. http and https are different services, we need to address them individually.

If i read you right, you've server's A & B which are both exposing https services. You've a load balancer C sitting in front.

You want C to load balance connections between the two servers. You don't mention installing agents on A or B and you dont mention screen scraping mod_status or anything like that on A or B from C to make decisions about who's more loaded, so that means you're going for plain old basic round robin load balancing (nowt wrong with that!).

I'm guessing you haven't chosen DNS load balancing because there's only 1 public ip address available and it's not administratively possible to allocate a second IP to this service.

You want the encryption end points to be A/B and the client, C must pass it on without decyphering (are you sure? you're sure you're sure? absolutely sure? ok! it's just that having C handle encryption and decryption and having A/B handle application functionality would be a common method of breaking out an n-tier app for horizontal scaling).

Given all this... an apache in reverse proxy will handle all this in it's sleep when running on C.

---

