---
title: "BIND Setup: Can't dig from outside LAN"
date: 2006-11-12
forum: Server Platforms
---

### Post by damonc on 2006-11-12
Hi all,
I have been trying to set up bind DNS on my testing/learning server but have gotten myself stumped. I have done a bit of reading and I think I have set up my config files correctly.

I have a registered domain which i want to host at home.

My questions:
1. Should I use Bind as a caching nameserver as well as a nameserver for the domain?

2. When I dig my domain name via PuTTY accross the LAN, the output seems OK, but when I do a DNS lookup on the domain from [dnsstuff.com]("http://www.dnsstuff.com") it times out.

Any ideas? I can post contents of files if it's needed.

On the topic of posting file contents, why are IP addresses and domain names often disguised by posters? Aren't they all out in the public domain eventually anyway? If it's for security reasons, what is safe to post and what should be kept secret?

Sorry for this post jumping around a bit. any help appreciated as always.

---

### Post by elst on 2006-11-12
1. IIRC, BIND automatically caches. A "caching" or "caching-only" BIND server is one that manages no zones and therefore relays all lookups (caching the results). It's kinder on other people's servers to cache your queries.

2. Your server plus one other server must be registered as authoritive for your domain. Once that happens it takes some hours for the info to propagate across the DNS system - it's expected that it takes at least 24 hours for new domains to fully propagate.

Having said that, by all means post named.conf if you aren't sure of your settings. BIND isn't exactly user-friendly...

WRT to masking host information, anything that you post anywhere on the Internet is easily searchable and available for eternity (Google for the Wayback Machine) to everybody, including the most peculiar folks you never want to meet. So it's really just good practice to avoid posting *any* information that you wouldn't shout across a room full of strangers.

---

