---
title: "Setting up Bind9 for a Primary DNS and name server on a VPS"
date: 2011-01-07
forum: Server Platforms
---

### Post by maxsteele on 2011-01-07
Hey everyone, I will preface by saying I am new to Ubuntu, but I have a networking background.

I have a VPS from 123systems.net .  I purchased a domain, craftersrealm.com, from them as well, expecting them to attach this domain to my VPS.  When I purchased the domain, that was all I received - the domain.  The interface on their site wants me to put in a name server to use.  I sent them a support ticket and they told me I would need to install some sort of webserver to manage the domain from there.  

Realizing I wasn't going to get any assistance from them, and that I'd have to set up DNS and a name server on my VPS myself, I started researching on my own and found bind9.

At this point, I have bind9 configured on a local level.  I can ping craftersrealm.com, [www.craftersrealm.com](www.craftersrealm.com), and ns.craftersrealm.com while sshing to the server.  Dig also shows the appropriate domain name and IP address.  However, none of these are available over the public internet.  It has been more than 2 days in case there was an issue of propagation.

Where I am stuck right now, is what do I need to do with bind9 to make my domain's name server available publicly, so I can then enter it on 123systems.net for my domain?  I'm not sure I have this part configured correctly, and I'm also not sure which part it is to have this domain seen on the public internet.

If you need to see any configuration files, I can copy those here.  Please let me know which ones and I'll post them.

Thank you in advance for your assistance!

---

### Post by greekspartan on 2011-01-15
For the world to see your website, you need two DNS servers. You have already set up yours, but you need to set up another one (there are free service providers that can do this). Once you have these two DNS servers (name servers) set up, you need to login to your control panel and add them to your domain.

---

