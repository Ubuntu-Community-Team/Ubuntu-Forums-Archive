---
title: "Configuring Postfix as relay server"
date: 2015-12-14
forum: Server Platforms
---

### Post by jmish1987 on 2015-12-14
So far I've searched Google, Bing and StackExchange and cannot find a specific guide or explanation on how to do this, only how to use Google SMTP or my ISP's SMTP server. I don't want to do that if I can avoid it, I would like to host my own remote postfix relay server.

I have a Virtual Server at home running Virtualmin with Postfix, Dovecot, so on and so forth on Ubuntu. I also have a need to send email from a couple of other machines on my home network. I have 4 domains that email would come from:

domain1.com <- Primary
domain2.com
domain3.com
domain4.com

The issue with this is I have Comcast, and it blocks port 25 in and out.

So, I am renting a small VPS outside my network in the hopes that I can relay email through it both in and outbound on port 587. 

My home network is reachable from the internet using the hostname 'home.domain1.com'. I also have a VPN which all of my machines and my remote postfix server are connected to.

The remote postfix server is reachable using 'mail.domain1.com' and is also running Postfix, but with no configuration.

I would like for myself to send email from my home network and it be relayed through the remote server and onto its destination, definitely appearing as the origin domain (which is why Google SMTP or my ISP's SMTP won't work, the email has to appear to come from the user/domain it was sent from, not my gmail or ISP email). Likewise I want to put mail.domain1.com in my MX records and have it receive email and forward it through the VPN and onto my home server.

Is there an existing tutorial out there or anything that people can guide me to perhaps set this up. I'm fairly familiar at least with Postfix's different settings and such, but still no idea how I would accomplish this, specially where the email still appears to come from [email]user@domain3.com[/email], not [email]user@mail.domain1.com[/email] after its relayed.

Thanks for the help you can provide to me.

---

