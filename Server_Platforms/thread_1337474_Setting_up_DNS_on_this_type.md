---
title: "Setting up DNS on this type"
date: 2009-11-25
forum: Server Platforms
---

### Post by Cardale on 2009-11-25
I was thinking about hosting my own domain and wanted to setup a DNS, but I was wondering if I could even do that.  If I host my own domain name I don't need a fixed IP if my IP changes it will resolve with the name system?  How does this work if it is a DHCP system?  Does it matter?

---

### Post by doas777 on 2009-11-25
you can set up a dns server for your local intranet(s) and have it forward onto the public servers in the case that it is an external server. that way you can just point to one server to handle both internal and external queries.

you cannot host your own domain unless you register it with a registrar, and for that you need a static IP, or to use a service like dydns or no-ip. 

you can set up internal dns to handle automatic registrations for dhcp clients on your lan, but I can't help you with that.

---

### Post by Cardale on 2009-11-25
Thanks for the reply.  The reason why I was asking is I do use dyndns at the moment and I want to beable to have my own email domain names and hopefully not pay the custom dns fees from dyndns.

---

### Post by doas777 on 2009-11-25
I'm afraid there is no getting arround it. DNS is there so that clients can get to you, so the name of your domain (and your IP) have to be listed in whatever public dns server they use, where ever they are. the only way to do that, is to register the name globally, and pay the associated fees.

I know it seems like fees are a pain, but they help internet governance, in that the most crime comes from the cheapest tld's (.info last I looked).

---

### Post by Cardale on 2009-11-25
Thanks for the reply.

---

