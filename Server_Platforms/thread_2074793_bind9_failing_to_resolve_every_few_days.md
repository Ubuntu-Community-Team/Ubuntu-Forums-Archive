---
title: "bind9 failing to resolve every few days"
date: 2012-10-22
forum: Server Platforms
---

### Post by pegruder on 2012-10-22
So as the title says - I have bind9 failing to resolve every few days.  I could be sitting there browsing the web, and all of a sudden, I cant get to pages.  I can ping via IP, but I cant resolve any external dns.  Now that I think of it, I think I *can* resolve internal DNS.  I'd have to double check if the issue comes back.  

So far its happened twice inside of a week.  A restart of the process has fixed the issue both times.  So far the only change I've made is changing from the OpenDNS servers in the forwarders section, to google's dns servers.  Ill have to report back in a few days to see if it comes back.  Anyone experience this issue before?  

Im running Server edition 12.04 LTS, all latest updates installed.

---

### Post by anonymouschief on 2012-10-22
I have had a similar issue caused by UFW blocking the DNS server addresses in the forwarders section of my Bind config. In my case it was the 4.2.2.2 - 4.2.2.5 servers. The fix was to set a port 53 ALLOW rule for these IPs in UFW.

---

### Post by pegruder on 2012-10-23
> **anonymouschief said:**
> I have had a similar issue caused by UFW blocking the DNS server addresses in the forwarders section of my Bind config. In my case it was the 4.2.2.2 - 4.2.2.5 servers. The fix was to set a port 53 ALLOW rule for these IPs in UFW.

I just double checked, UFW is currently in inactive mode.  This server is currently behind a firewall so I may have to open it up there if thats causing the problem.  Ill wait it out first since I changed DNS servers.  I've read how OpenDNS isnt truly "real" dns, in that if it cant find something, it returns pages with ads.  Maybe its when I cant find a page, its returning that or something funny to bind, causing it to lock up or crash.

---

