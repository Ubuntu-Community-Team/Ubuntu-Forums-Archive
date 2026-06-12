---
title: "DNS cache?"
date: 2012-05-10
forum: Security
---

### Post by computeratin on 2012-05-10
I know that there are nowhere near as many security concerns with *nix as doze. But I think this is an idea that should cross OS's?

One of the few things I have set up in doze right now that I'd like to keep is DNS resolution. 

In doze I turned off the DNS cache service. Not so much directly for system security per se. I know about cache poisoning, etc. But I did it because doze will resolve any address that you ask it to. Even to known malicious sites.

To prevent that you have to shut off the local cache and then I pointed my router at OpenDNS.org b/c doze will default to the router to resolve if the cache service is disabled.

I've been reading that the UB DNS cache is designed to be more secure than the doze cache. But, unless it has a filter (or I can set one up?), I'd rather point it at or default to the router to resolve DNS.

How do I achieve that?

---

### Post by Hungry Man on 2012-05-10
Ubuntu doesn't have a DNSCache. 12.04 has the capability to have one natively but as far as I know it is not active. Browsers cache (per session) and prefetch DNS anyways.

---

### Post by computeratin on 2012-05-10
> **Hungry Man said:**
> Ubuntu doesn't have a DNSCache. 12.04 has the capability to have one natively but as far as I know it is not active. Browsers cache (per session) and prefetch DNS anyways.

HMMM, maybe I'm confused? 

I was just reading over at another forum where somebody had a similar question. But their question was more along the lines of preventing cache poisoning and all the replies basically said don't sweat it, you don't need to disable it, UBs cache has been built to be secured against that kind of stuff.

Ergo: It has one and it runs out of the box?

Added for clarification: (Reply at another forum)

> This dnsmasq server isn&#8217;t a caching server for security reason to avoid  risks related to local cache poisoning and users eavesdropping on  other&#8217;s DNS queries on a multi-user system.Like I said, I'm not worried (too much) about things like cache poisoning with UB. (B/c they actually care about that kind of stuff, unlike some who shall remain nameless!)

I'm looking to keep it set up so that OpenDNS filters for me. Or install a filter?

---

### Post by Hungry Man on 2012-05-10
Like they say, it doesn't cache. It's not that it's caching in some special secure way it simply doesn't do it.

---

### Post by computeratin on 2012-05-10
OK, trying to make the complete crossover. I know this silly stuff in doze.

In doze, to point at the filter I have to kill the cache.

No need to kill the cache here: Check.

So how do I point at the filter?

It's a nice filter. I like filters. This one filters all kinds of bad stuff, not just exclusively doze bad stuff. 

I'd like to keep it.

---

