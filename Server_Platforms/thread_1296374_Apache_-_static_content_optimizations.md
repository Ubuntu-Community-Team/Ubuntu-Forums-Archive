---
title: "Apache - static content optimizations"
date: 2009-10-20
forum: Server Platforms
---

### Post by AwkwardSilence on 2009-10-20
I am setting up a pair of dedicated static web servers and would like to optimize the configuration. I am running Apache 2.2 on the dynamic web servers, so my plan was to stick w/ Apache 2.2 for the static servers as well. I've ran lighttpd in production before, but got frustrated with it after bugs (memory leaks, proxying, etc.) wasted a bunch of my time. After that, I decided to use more mainstream packages when possible. If the requests are handled that much faster though, then I would consider using a lighter web server again.

Specs:
Ubuntu Server 9.04 x86, 2 GB RAM, 2x Dual-core Xeon 3.0GHz, Dual gigabit NICs
Dedicated server w/ minimal install: Ubuntu OS + ifenslave (for dual NIC bonding) + apache2

Usage:
Will handle almost all of our sites static content (images, banners, downloads, etc.). At times, there will be about 1,000 70KB images all requested at the same exact time. (7 different images w/ multiple users requesting the same 7 files)

Questions:
- I'll be installing 64-bit edition of 9.04 server - Any idea on how much I'll benefit from this over a 32-bit installation?

- Since this is a dedicated server, is there anything that I can do to utilize the full 2GB of RAM? My test installation uses less than 200MB. Would it help to use something like 1.5GB for memory caching the recently requested files? If so, will mem_cache mod do it?

- Any other config options to optimize from the default Apache2.2 package installation or the server in general?

- When testing w/ 'ab', I ran into a few issues. I had to increase the ulimit -n to handle more concurrent requests. However, I've been running into a "Connection reset by peer" and only 85-90% of files get served. This is with 10000 request and 1000 concurrent

- For the spikes with 7 images getting requested by 100-200 users at the same time. Any specific optimizations that would help with that? Anything that would load or cache those 7 files and efficiently server them to the other users?

- If there is a better web server for this, what do you recommend? nginx, lighttpd, etc.?

*Note: Web server will be used for multiple domains, so virtual hosting needs to be supported

---

### Post by i.r.id10t on 2009-10-20
Check the pages at library.linode.com - they have a thing on configuring things to survive a slashdotting or farking.  

That said, my VPS only has 360mb of ram and it has handled a few farkings for a largeish image several times without a hiccup.

---

