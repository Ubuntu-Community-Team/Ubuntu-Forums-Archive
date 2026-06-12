---
title: "Couple of simple server questions....video card/DNS"
date: 2008-01-26
forum: Server Platforms
---

### Post by HautingLu on 2008-01-26
I inherited and old 400 MHz machine that I loaded 7.10 server on.

Anyways, on the back it has a PCI video card with an S-Video and a yellow RCA plug.

**How can I tell if it's in an input or output (stupid question I know).**

lspci outputs:

> 01:00.0 VGA compatible controller: nVidia Corporation NV4 [RIVA TNT] (rev 03)

I have a wireless security camera I'd like to hook up to it if possible.


Also, just wondering but if i buy a domain name and want to run some simple web pages, how does the domain link to my server that has a dynamic IP?

Thanks :biggrin:

---

### Post by freebeer on 2008-01-27
> **HautingLu said:**
> 
Also, just wondering but if i buy a domain name and want to run some simple web pages, how does the domain link to my server that has a dynamic IP?


Is your server behind a router?  If so, give the server a static internal IP address and forward ports in the router to your server.  If you have a changing IP address from your ISP, then you'll really want something like what is offered from DynDNS.org.  They offer a free service where you get a domain name which points to your external IP address.  You then run a script on your server that checks to see if your IP address has changed.  I it has, it updates DynDNS's entry for your domain and soon traffic will be flowing to your new IP addy.

---

### Post by HautingLu on 2008-01-27
> **freebeer said:**
> Is your server behind a router?  If so, give the server a static internal IP address and forward ports in the router to your server.  If you have a changing IP address from your ISP, then you'll really want something like what is offered from DynDNS.org.  They offer a free service where you get a domain name which points to your external IP address.  You then run a script on your server that checks to see if your IP address has changed.  I it has, it updates DynDNS's entry for your domain and soon traffic will be flowing to your new IP addy.

Thanks. I'm familiar with this. I've been using DynDNS and the stuff you mentioned because it's behind a router. But if I buy a domain like [www.MySite.com](www.MySite.com) from GoDaddy, how does it link my URL to my IP?
Maybe my wording isn't clear........


Any suggestions about the video card?

Thanks.

---

### Post by freebeer on 2008-01-27
Well, the way I understand it, you really need a static IP address from your ISP for that to work.  (Sometimes they'll offer it, but usually at additional cost.)  You could, I suppose, monitor your IP address then change your entry when it changes, but chances are you'd have to do that manually, and the propagation of the change may be a lot slower.  I'm not positive about that, of course, but those seem to be likely issues you should consider.

I don't know about your card, but you can probably do a google search on the technical specs of your card and see what they say.

---

### Post by smileypaul on 2008-01-29
err.. i dont use godaddy, but you should be able to set up a forwarder... it would forward to your dyndns address, and away you go. It may be in your best interest to spend a few bucks on hosting though unless space is an issue

---

