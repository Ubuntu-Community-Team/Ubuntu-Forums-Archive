---
title: "Why is this faster than that?"
date: 2010-05-05
forum: The Cafe
---

### Post by t0p on 2010-05-05
[Invisible Browsing VPN]("http://www.ibvpn.com/") recently set up a new server, in the Netherlands, and I was fortunate enough to get a free account on the server.  I have observed something strange.  I regularly access the internet via a 3G cellphone, and when I do this directly, the system monitor generally reports download speeds of about 40-60 KiB/s.  But when I go through the ibvpn server, the system monitor reports much faster speeds - usually 60-80 KiB/s, and often higher.  Reported speeds of over 100KiB/s are not an unusual occurance if I go through the server!

I can't see any way that the VPN server can accelerate throughput.  So the only explanation I can think of is that my cellphone service provider is deliberately providing me with an inferior service even though I am a paying customer.  Is that a reasonable thing for me to conclude?  And if it is so, is it a reasonable thing for a cellphone service provider to do?

---

### Post by 3rdalbum on 2010-05-05
Thanks for the link, I'd been looking for something like this for when Australian internet gets filtered.

Sorry I can't answer your question, except that possibly when you're using the VPN your traffic is going through fewer jumps to reach your destination.

---

### Post by ssam on 2010-05-05
they might put http requests through a transparent proxy to 
*save them bandwidth
*apply extra compression
*filter what you can see
*other useful or devious things

they can't proxy the vpn (they dont need to filter VPN, because anything you download through the VPN looks like it went to the VPN host not them).

---

### Post by eriktheblu on 2010-05-05
> **t0p said:**
> ... the only explanation I can think of is that my cellphone service provider is deliberately providing me with an inferior service even though I am a paying customer.  Is that a reasonable thing for me to conclude?  
Yes, but there could be other explanations.

My experience has been that cellular companies deliberately neuter their capabilities in order to sell what should be standard features as extras. A phone I purchased 4 or so years ago had built in games that the service provider disabled (but they were still on the phone).

---

### Post by t0p on 2010-05-05
So it would appear that going through  a vpn is a good idea if you use a cellphone provider to connect to the internet.  Only problem is you generally have to pay for a decent vpn service.  Free services, like [ItsHidden.com]("http://itshidden.com") and [Your Freedom]("http://your-freedom.net"), are slow as heck.  But some premium services give out free accounts: ibvpn gave away 100 accounts on its Dutch server to celebrate the new service, and I was one of the lucky 100.  They also give away 30 one-month accounts each month on each of their servers, plus they dish out one-day trial accounts to anyone who asks, and they'll give accounts to frequently visited bloggers who give them fair reviews.  And ibvpn aren't alone in this behaviour: I had a freebie with [AceVPN]("http://www.acevpn.com") in the past.

---

