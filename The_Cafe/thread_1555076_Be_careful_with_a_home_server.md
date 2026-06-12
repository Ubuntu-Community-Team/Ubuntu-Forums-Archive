---
title: "Be careful with a home server"
date: 2010-08-17
forum: The Cafe
---

### Post by phaed on 2010-08-17
I set up a LAMP server on my home computer to play around with.  Apache was serving a blank web page.  Network traffic (or lack thereof) would reveal that I was not using it for nefarious purposes. However, my ISP did a "routine port scan", noticed that I had ports 22 and 80 open, and blocked my internet access.  When I attempted to get on the internet, I got a page telling me I had (possibly) violated their terms of service and that I should call a number, which is when they told me what happened.  They have a policy against "providing network services," whether it's for yourself or others.  

I'm connected again, but be careful before you try this at home.

The agent told me that my violation was unusual, though.  Usually he handles copyright cases. :-)

---

### Post by juancarlospaco on 2010-08-17
*Change dah portz or change isp* :)

---

### Post by Austin25 on 2010-08-17
Which isp's allow you to provide network services? Does Mediacom?

---

### Post by whiskeylover on 2010-08-17
> **phaed said:**
> I set up a LAMP server on my home computer to play around with.  Apache was serving a blank web page.  Network traffic (or lack thereof) would reveal that I was not using it for nefarious purposes. However, my ISP did a "routine port scan", noticed that I had ports 22 and 80 open, and blocked my internet access.  When I attempted to get on the internet, I got a page telling me I had (possibly) violated their terms of service and that I should call a number, which is when they told me what happened.  They have a policy against "providing network services," whether it's for yourself or others.  

I'm connected again, but be careful before you try this at home.

The agent told me that my violation was unusual, though.  Usually he handles copyright cases. :-)

Which ISP is this? Verizon/Comcast let you host servers for personal use (HTTP for example) as long as they're not abused.

---

### Post by juancarlospaco on 2010-08-17
*i need an UPS, so is not production ready, mine is off, but isp dont care of ports.*

---

### Post by kaivalagi on 2010-08-17
Yeah, just change port numbers!

I have no issue with my ISP, based in the UK with VirginMedia cable. I only use it for personal use mind you as serving pages on a standard domestic connection is painful, the upload speed just isn't up to scratch really

---

### Post by samalex on 2010-08-17
To the OP, what ISP are you using?  I'm with TW, and though I don't have a server running now, I ran WWW, SSH, and Telnet servers from home for about 8 years with no problem.  It is against TW's terms to do so, but my thought is as long as they don't complain and I'm not sucking much bandwidth I didn't care.  And if they did, they could let me know and I'd pull it, as happened to the OP.

I equate it to the BBS days when people ran BBSes and Answering Machines from their home phones, and remember there was a time when it was against the terms to even have an answering machine at home.  I figure eventually ISP's will come around that not allowing servers at home is outdated.  I mean heck most ISP's already cap outgoing bandwidth to less than stellar, so it's next to impossible to run anything professional from a home broadband connection.  Mine's capped at like 128kbps, which yeah makes for a slow web server.

Sam

---

### Post by Austin25 on 2010-08-17
Do it through the wifi at the cafe. Muhahah...

---

### Post by Legendary_Bibo on 2010-08-17
> **Austin25 said:**
> Do it through the wifi at the cafe. Muhahah...

He could hide the server behind a plant or something.

---

### Post by SoFl W on 2010-08-17
> **whiskeylover said:**
> Which ISP is this? Verizon/Comcast let you host servers for personal use (HTTP for example) as long as they're not abused.

Really?  I thought Comcast blocked port 80 (and others) because I used to have them.  I have Time Warner now and they allow 80 opened, but upload speeds are SLLLLLOOOOW.  I had a friend try to grab a file and he said it was too slow.

---

### Post by LowSky on 2010-08-17
Use a different port. find an unused port number and tell apache to use that instead of port 80.

[http://www.no-ip.com/support/guides/web_servers/isp_block_port_80.html](http://www.no-ip.com/support/guides/web_servers/isp_block_port_80.html)

---

### Post by pricetech on 2010-08-17
> **Legendary_Bibo said:**
> He could hide the server behind a plant or something.

Brilliant.  I like it.

Seriously OP, read the terms of service.  Whether it makes sense or not, it's the terms you agree to when you choose an ISP.

And to those who would flame me for saying that;  Yes it seems silly to block a personal web server, an FTP server shared with a few close friends, etc. but not everyone's purpose is ambivalent.  The ISP is just protecting its users as a whole from those few who would abuse the service.

Sadly, that's the kind of world we live in.

---

### Post by Austin25 on 2010-08-17
I wonder if Mediacom does this?
I want to set up a vpn server because our school has a fire wall.

---

### Post by whiskeylover on 2010-08-17
> **SoFl W said:**
> Really?  I thought Comcast blocked port 80 (and others) because I used to have them.  I have Time Warner now and they allow 80 opened, but upload speeds are SLLLLLOOOOW.  I had a friend try to grab a file and he said it was too slow.

I always had 80 open with Comcast. Now I'm with Verizon and I specifically asked them before I signed up with them if they blocked 80, 22 and other common ports. Someone posted a link to a webpage on verizon.com saying that they don't. 

Let me see if I can find that link.

---

### Post by phillw on 2010-08-17
::sigh:: at your ISP :-(

If it is causing you a problem please have a quick read of [An alternative](https://wiki.ubuntu.com/phillw#Web_Hosting) It will be middle of September to have everything all up and running. 

As you can see, you get pretty much full server access (own php.ini etc.) You just need to have LAMP installed on your desktop system [ LAMP class](https://wiki.ubuntu.com/phillw#LAMP) along with something like [FileZilla](http://filezilla-project.org/) which is available via Synaptics to be able to do transfers.

I'd also raise a note of caution about setting up ssh at home, as I got one bit wrong and got royally hacked.

The slides I gave as part of my class have some excellent links on them, the server area on these forums is an excellent resource.

Regards,

Phill.

---

### Post by kenweill on 2010-08-17
> **phaed said:**
> I set up a LAMP server on my home computer to play around with.  Apache was serving a blank web page.  Network traffic (or lack thereof) would reveal that I was not using it for nefarious purposes. However, my ISP did a "routine port scan", noticed that I had ports 22 and 80 open, and blocked my internet access.  When I attempted to get on the internet, I got a page telling me I had (possibly) violated their terms of service and that I should call a number, which is when they told me what happened.  They have a policy against "providing network services," whether it's for yourself or others.  

I'm connected again, but be careful before you try this at home.

The agent told me that my violation was unusual, though.  Usually he handles copyright cases. :-)

I thought port scanning can be blocked. As ping can be blocked, never to respond to the sender.

---

### Post by t0p on 2010-08-17
> **kenweill said:**
> I thought port scanning can be blocked.-

But how many people actuallydo it?  Five? Six?

> **kenweill said:**
> 
As ping can be blocked, never to respond to the sender.

If pesky kids rang your doorbell and ran away a few times, would you tun off the doorbell and have nothing more to do with visitors.  That'll teach them kids, right?

---

