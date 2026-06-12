---
title: "ufw port forwarding"
date: 2008-04-05
forum: Security Discussions
---

### Post by kroenecker on 2008-04-05
Could someone explain how I would use ufw to forward a port from my desktop (which is acting as a gateway) to a computer on my internal network?

---

### Post by bon_the_one on 2008-06-27
I'd also like to know if this is possible. I have a Mythbuntu backend running UFW which is connected to my cable modem. Then I have a PC in my home office. The machine on the cable modem is on 10.0.0.1 internally, and the office PC is 10.0.0.2. 
To use XTen's XLite properly with my VOIP provider I'd ideally like to forward everything coming in to port 5060 on the Mythbuntu 'gateway' machine to 10.0.0.2 port 5060. 
I know I could just bounce everything forward, but I want to be able to ssh into the Gateway remotely, but port 5060 should divert directly to 5060 on another machine.

I could do this with a router I guess. That means going to buy a router tho, plug the cable modem into that, configure it, and then plug both machines into that. However most routers run a cut down Linux tho, so there *must* be a way to do the same with Ubtuntu?!

If anyone can offer any advice I'd really appriciate it,

Bon

---

