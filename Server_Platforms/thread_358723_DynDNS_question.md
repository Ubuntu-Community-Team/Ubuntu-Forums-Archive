---
title: "DynDNS question"
date: 2007-02-11
forum: Server Platforms
---

### Post by bgolub on 2007-02-11
Here's my scenario:

I currently have 2 domains on 1and1.com registered.  Each of them points to my server on campus where I have a static IP and everything works beautifully.  In May I'll be graduating so I won't have access to this static IP anymore and don't really want to start paying for hosting if I don't have to, plus I like to be in complete control of my server.

I'm wrapping my head around ddclient and DynDNS but I don't completely understand one thing.  Using DynDNS and ddclient I understand that I can get my-site.dyndns.com to point to my server despite it being a dynamic IP because my server will tell DynDNS to change my-site.dyndns.com to the new IP.

My question is, in my 1and1.com control panel I can only put in an IP address or a custom name server.  How do I point my domain to my-site.dyndns.com?  I'm not sure if my-site.dyndns.com is going to be a static IP, if it is then I could just point my 1and1.com domain to it.  But if it's ALSO dynamic then I don't understand exactly how this name server business works.

Thanks in advance!

---

### Post by bgolub on 2007-02-11
Ah, looks like I need to use their Custom DNS service? [http://www.dyndns.com/services/dns/custom/](http://www.dyndns.com/services/dns/custom/)

It's $24.95 for a year...not bad but I was hoping I'd find something that was free.

EDIT: I found zoneedit ([www.zoneedit.com](www.zoneedit.com)).  It's free for the first 5 domains.  A domain will count as 2 domains if it goes over 200MB usage, 3 domains if it goes to 400MB usage.  So I should be completely set with 2 domains.  I don't see myself getting anywhere CLOSE to 200MB (1000000 DNS queries) anytime soon for my simple blog/gallery.

---

### Post by PurplePenguin on 2007-02-11
Yes, if you want to use your own domain name, you'll need to pay $24.95 a year.  If you don't care about the name and don't mind having a subdomain (ie. whateveryouwant.dyndns.org), it's free.  

It's actually extremely easy to get Ubuntu Server up and running with DynDNS.  I went from having an old system with a blank HD to a live server with DynDNS in about an hour (and I was a first-timer!).

---

### Post by thornomad on 2007-02-16
What is the name of the software client that runs in the background on the server and updates the IP address automatically ?  I wanted to setup that Custom DNS server myself ... wasn't sure what the program was called though.  Is it available through apt-get (regular repositories) ?

---

### Post by Ramses de Norre on 2007-02-16
> **thornomad said:**
> What is the name of the software client that runs in the background on the server and updates the IP address automatically ?  I wanted to setup that Custom DNS server myself ... wasn't sure what the program was called though.  Is it available through apt-get (regular repositories) ?

ddclient, it's in the repo.

---

### Post by Brazen on 2007-02-16
Just FYI, most soho routers have a built-in dyndns client, so your dynamic dns is controlled right from your router.  I have a linksys wrt54gs, the setup was simple through the web interface and it works like a charm.

---

