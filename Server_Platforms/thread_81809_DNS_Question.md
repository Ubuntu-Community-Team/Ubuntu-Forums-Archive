---
title: "DNS Question"
date: 2005-10-25
forum: Server Platforms
---

### Post by Rollo Tamasi on 2005-10-25
Hi lads, i've setup my server and its accessible thru any browser when i type in the server's IP address. How is it possible to transform that IP address to a DNS address such as mywebsite.com ? 

The IP address i have is static and i know my ISP's DNS settings but i'm going to throw caution to the wind and find out more about this in case i cause any problems.

What would happen if i use my ISP's DNS settings when setting up a dns address for my server. Is there any chance i can use a DNS service just with the static IP?

Cheers lads,
Cormac

---

### Post by kurtkraut on 2005-10-25
First of all, you need a domain. Once you have a domain, you will need an external DNS server (not the DNS server from your ISP).

There as some free DNS servers. I suggest [www.xname.org](www.xname.org) or [www.everydns.net](www.everydns.net).

You will have to configure in the system of your domain's registrar that your domain will be controlled by xname.org service, for instance.

In the xname.org system you will point ww.yourdomain.com to your static IP.

Then, be happy ;D If my english wasn't understandable, just ask again.

---

### Post by Rollo Tamasi on 2005-10-25
Thanks Kurt, your english is fine, i will check out both those sites.

Is there any application that you can install on your box to manage your dns settings? some kind of dns control panel?

---

### Post by markthecarp on 2005-10-25
[QUOTE=Rollo Tamasi]Hi lads, i've setup my server and its accessible thru any browser when i type in the server's IP address. How is it possible to transform that IP address to a DNS address such as mywebsite.com ? 

The IP address i have is static and i know my ISP's DNS settings but i'm going to throw caution to the wind and find out more about this in case i cause any problems.

What would happen if i use my ISP's DNS settings when setting up a dns address for my server. Is there any chance i can use a DNS service just with the static IP?

Cheers lads,
Cormac[/QUOTE]
I've been using [http://www.dyndns.org]("http://www.dyndns.org") for several years to do this. My server is behind a Linksys router. It's setup with a static local IP address. I use the dhclient package to manage changes in the external IP address. My cable access provider's dhcp servers assign a new external address every 12-18 months.

-mark

---

