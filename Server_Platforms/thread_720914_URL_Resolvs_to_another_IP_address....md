---
title: "URL Resolvs to another IP address..."
date: 2008-03-10
forum: Server Platforms
---

### Post by 67comet on 2008-03-10
Hello, I have a unique issue that started at 6:03am on the 9th of March. I use freedns.afraid.org as my dns and GoDaddy.com as my registrar. I've used these two for a few years on all of sites on my Ubuntu Server. Never really had an issue that wasn't something I did, but right now I'm in a mess I can't figure out.

All of my URLs seem to resolve at another IP address. I've reset GoDaddy's DNS server info to ns1.afraid.org (ns1,2,3 & 4), made sure afraid.org has my current IP address (and I use a cron ran script that keeps my IP current with them) yet still none of my URL addresses will resolve at my server.

I'm at a loss on where else to look but when I attempt to ping (from out side or inside my network) the ping times out, but it hands me a URL that is NOT mine. 122.145.71.122 when it should be (currently) 122.145.71.123. Even when I do a "What's my IP" search on Google it comes up with the .123 address.

Help?
Thank you,
Justin

---

### Post by astrotech226 on 2008-03-10
What host names and domain name are you having trouble with?

Then, what type computers are you using to check the IP addresses?  Windows?  Linux?  You might have a dns caching issue with local dns servers or on the host itself.

---

