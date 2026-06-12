---
title: "How To go fully IPv6 with Cloud Flare, a web server with both ipv4 and ipv6?"
date: 2012-08-26
forum: Server Platforms
---

### Post by THPubs on 2012-08-26
I have setup an Nginx server in a machine which have both ipv4 and ipv6 addresses. Currently, its connected to CloudFlare and only use ipv4. I have 1 ipv4 address assigned to the web server.

Now what I want is, to become fully ipv6. Then connect to CloudFlare. So, if an ipv4 user comes to the site, CloudFlare will make sure that he can visit my ipv6 only site! Does it happen like that?

What is the best way to implement ipv6 on my server? Only ipv6 or both versions? How to implement it (In CloudFlare dns and in Nginx configuration file). Please help!

---

### Post by sanderj on 2012-08-28
IMHO Fully IPv6 is something else than IPv6-only.

You can make a server IPv6-only, but that way 99+% of the devices in the world can't visit you anymore as they are IPv4-only.

IPv4 and IPv6 will co-exist 'dual stack' for the coming years; devices will need to have IPv4 **and** IPv6.

---

### Post by d4m1r on 2012-08-28
I would personally contact Cloudflare on a guide on how to setup their service to work with ipv6 and yes, it would depend on whether you want ipv6 only, or both.

Not sure if you could even set it up through them to route both your ipv4 AND ipv6 traffic but they'd be able to tell you if you can or can't...

---

