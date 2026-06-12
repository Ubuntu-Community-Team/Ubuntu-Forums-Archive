---
title: "Forwarding a URL driving me nuts"
date: 2009-02-09
forum: Server Platforms
---

### Post by C0D3X on 2009-02-09
Hi guys,

I have been scratching my head trying to figure this out for some time now.

I have a Domain name hosted with an external company. I use their DNS to forward a few sub-domains to my static IP.

Eg. 
sbs.mydamain.com (SBS 2003 Exchange Server)
im.mydomain.com (Instant Message Server on Ubuntu Server)
crm.mydomain.com (Contact Database on Ubuntu Server)

So only the sub-domain changes.

I have Ubuntu 8.04LTS with Bind and my favourite thing in the world, Webmin.

My Linux server has 2 NIC's and acts as a Gateway. I do this because I want to protect my Internal network, espescually the vulnerable SBS 2003 Exchange Server.

I want to send all Ports on the Router to the Ubuntu Server, then have the Server forward the URL for sbs.mydomain.com to the SBS 2003 Server.

Please note that I am a bit of a beginner to Linux. I chose Linux as a Gateway and Web Server because of it's fantastic Security. Please be gentle with your explanations.

Thank you in advance.

---

