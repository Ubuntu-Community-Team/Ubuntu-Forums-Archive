---
title: "How do I shape the speed of specific ports?"
date: 2007-08-07
forum: Server Platforms
---

### Post by some_random_noob on 2007-08-07
I just found out that webhosting is a complete ripoff, so I want to host my site using my own Apache2 server. I know how to do all of this, but the problem is that I only have a 1GB datacap and a very very slow ADSL1 connection. I want to slow down the outgoing port 80 (http) traffic, so that I can still use my computer to do stuff while people browse the site I'm hosting without it getting laggy.

Are there any tools out there that I can use to slow down traffic on SPECIFIC ports? I really need to be able to do this - you could save me $20nzd a month! :D

Edit: Preferably something I can get via apt-get.

---

### Post by HermanAB on 2007-08-08
Google for 'linux iptables rate limiting'.

Cheers,

Herman

---

### Post by some_random_noob on 2007-08-08
> **HermanAB said:**
> Google for 'linux iptables rate limiting'.

Cheers,

Herman
Damn, "rate limiting"? I was googling for "throttling" and "shaping". Oh well thanks anyway :) 

I should probably just get another computer for my server, it would be so much easier - I've learnt how to shape speeds, just not for specific ports. Having two computers would separate things and make it easier...

---

### Post by HermanAB on 2007-08-08
The rate limiting module is very useful. You can stop all kinds of evil with it, from ping floods to ssh password attacks, to the slashdot effect.

Cheers,

Herman

---

