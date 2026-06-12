---
title: "Ubuntu webserver (LAMP) for google (sad story)"
date: 2024-03-07
forum: Server Platforms
---

### Post by alebalweb on 2024-03-07
Let me tell you a little story...

My server has always been a small LAMP based on ubuntu, and first there was varnish, and everything was quite nice... then https and no more varnish...

With varnish gone, visits to my websites from search engines (Google) were greatly affected, I tried to compensate by optimizing the server... Memcached, Apcu, Opchache, mod_headers mod_expires in htaccess, and cache in web page headers.

My sites have become very light, very fast, wonderfully usable, my website pages instantly appeared out of nowhere in a magical poof!

But visits and earnings have collapsed, at the worst moment $30 a month...

I blamed the search engine, not my perfectly and wonderfully configured little server...

Then one day something happened, I had to completely reinstall a new server, and given the few results and earnings I didn't want to start reconfiguring a perfect server... I put a LAMP online without too many pretensions, and without any cache.. .

And visits from search engines have returned... and with them earnings in a few months have gone from $30 a month to $1500-2000 a month at the best time, now around $6-700 a month...

But the doubt has always remained, basically I just removed the caches, now my websites are slower and heavier, but somehow google likes them more now...

Is there anything else I can do on my server to make google like my websites, even if it goes against all obvious and reasonable logic?

Has anyone else unfortunately had stories like mine and perhaps discovered other optimizations or configurations on Ubuntu servers (or LAMP in general) that annoy Google?

---

