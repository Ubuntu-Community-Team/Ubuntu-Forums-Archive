---
title: "DNS subdomains migration Best Practices"
date: 2013-01-09
forum: Server Platforms
---

### Post by grigio on 2013-01-09
Hi, I'm looking for some best practices about how to manage dns and subdomains.

The situation is quite basic I've a couple of domains and ~20 subdomain.
Currently the registrar (Godaddy) points to the hosting's DNS nameserver (Dreamhost), so I use the hosting panel to create new subdomains.

In the near future I'll move to a VPS on a different provider, so I'll also have to find a different way to manage my domains and subdomains, here the options I see:

**Option 1: Manage domains in the registrar panel**
I can recreate all the subdomains structure in the registrar panel
```

blog.mydomain.com    -> my.vps.public.ip
mydomain.com        -> maybe.a.cname.somewhereelse
blog.otherdomain.com -> my.vps.public.ip
...

```
How could I minimize the down time? Because I have to host the domain in Godaddy before I can create subdomains for that domain??

**Option 2: Manage a DNS nameserver self-hosted in the VPS**
I will manage my own dns server via PowerDNS or other tools. I'll recreate the same subdomain structure and virtualhosts in advance so I just have to change the nameserver on the registrar to make the switch. I see a very little downtime in this way but is self-hosting a dns worth to do it?

**Option 3: Use the new VPS provider dns tool**
I won't be much different from now, but I've alwais recreate the subdomain structure. :(

Any suggestions are very appreciated! (Sorry for my english)

---

### Post by volkswagner on 2013-01-09
It's difficult to say what is best for you.  I'll just offer a little info on my recent experience.

I have serveral domains each with only a few subdomains.  I had a vps with a decent DNS manager, plus I was managing a couple domains that were not registered to me.  It just made sense to use the DNS manager at my VPS provider so I could centralize all the domains.

Recently the VPS provider warned me they were closing so I had to move.  I proceeded to move all domain and DNS using the new VPS's DNS manager.  Of course to do this I still had to go to the registrar and repoint to the new nameservers provided by the new VPS.

The last domain I had to move had several subdomains, some of which I point to a dynamic hosting domain from no-ip.com.  This is because I do some testing and such from my home server, which is on a dynamic ip.  When trying to add some of the CNAME records they would fail or not work as expected.  I could only summarize by saying the new VPS DNS manger was broken or not working properly.

This major issue forced me to rethink my DNS.  I ended up moving all DNS hosting to each respective Registrar.  Most are hosted at godaddy, which has a fairly decent DNS Manager panel.  Although this may end up being slightly more work when adding new sub domains in the future, it may be worth it.  In fact oddly enough, my new VPS has the DNS manager outside of the normal VPS control panel so it is not much different than logging into godaddy to edit DNS entries.  If I keep the DNS handled by godaddy, any future moves will not require me to recreate zones and all the subdomains.  For most of my domains, I'd only have to change the static ip for the top level domain name.

The fact is, you may not know what confronts you until you are fully aware of your future VPS providers DNS control panel functionality and performance.

I also think there is a slight benefit to having the DNS handled separately from my VPS provider.  I  use a cheap provider, if they go down for any extended period of time I can still repoint the DNS if needed to a backup server.  Failover would be nice but I'm not mission critical.

With godaddy, the free dns allows for 100 subdomains.  Included in the 100 are your name servers and mx records, etc.

---

### Post by grigio on 2013-01-11
> **volkswagner said:**
> It's difficult to say what is best for you.  I'll just offer a little info on my recent experience.
....

Thanks for sharing, I imagined something like that.

---

