---
title: "anonymousity  and proxy server"
date: 2006-07-27
forum: The Cafe
---

### Post by seshomaru samma on 2006-07-27
This is not an Ubuntu specific question ,but I hope someone can answer me:
If I use Tor as proxy server alongside Privoxy , can my ISP know which websites I've been to?

---

### Post by x64Jimbo on 2006-07-27
Your ISP can know pretty much anything about what websites you visit if they want to know badly enough. Using proxies definitely inhibits that, and if you can find one that uses SSL, you'll be in good shape and it's very unlikely that they'll try to crack your packets to see the urls you're visiting. ISPs often don't care what websites you visit, so I wouldn't be too worried about it.

---

### Post by BWF89 on 2006-07-27
I have Tor and Privoxy installed. Does useing these programs slow down your internet connection at all?

---

### Post by x64Jimbo on 2006-07-27
> **BWF89 said:**
> I have Tor and Privoxy installed. Does useing these programs slow down your internet connection at all?
Probably. I say this because your traffic is being forwarded and bounced around the "Onion network" so you're probably experiencing a slowdown unless your connection is slower by itself than all the delay incurred by the bouncing around.

---

### Post by j-strap2 on 2006-07-30
> **seshomaru samma said:**
> 
If I use Tor as proxy server alongside Privoxy , can my ISP know which websites I've been to?

So long as you have configured Tor and the application using it correctly, then your ISP cannot see which sites you are visiting. Only a very powerful adversary scanning multiple nodes within the Tor network could possibly identify your traffic. There is a problem whereby applications do not correctly use the SOCKS protocol to talk to Tor and make DNS leaks: that is, DNS requests are made to your ISP. Normally ISPs only log DNS requests made anyway, rather than the actual IPs of the sites you are visiting. It is these DNS request that you need to avoid.

> **BWF89 said:**
> I have Tor and Privoxy installed. Does useing these programs slow down your internet connection at all?

Yes, routing through the Tor network is slow - typically the speed of a dial-up connection.

---

