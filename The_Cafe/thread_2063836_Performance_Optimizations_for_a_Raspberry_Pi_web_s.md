---
title: "Performance Optimizations for a Raspberry Pi web server"
date: 2012-09-27
forum: The Cafe
---

### Post by physic.dude on 2012-09-27
Anyone who is a fan of the Raspberry Pi will know that it is somewhat limited, but quite capable of hosting a decent MySQL, Apache2, PHP, etc. web server.

I've set up mine as my own WordPress blog, which includes said fixings above, and it works just fine, except for the fact that there is an agonizing ~4sec TTFB (Time to first byte).

Would anyone have any advice on how to improve the server's overall performance? Perhaps considering the config files of various apps.

Quick hardware specs are:
- 232MB of RAM
- 700MHz ARM11 CPU (Overclocked to 1GHz)
- 32Gb UHS -1 / Class 10 MicroSD

---

### Post by lykwydchykyn on 2012-09-28
IME wordpress is quite heavy, and most themes having you downloading a boatload of files just to show the page.  It may also be referencing files (javascript libraries, css, etc) on a remote CDN, which would delay the page load even more.  

You can try using the network profiling functionality of Chrome/Chromium's developer tools to see which files are taking the longest to load.

You might also try switching to lighttpd (if WP supports it) to see if that runs any better.

Hard to advise more without knowing exactly where the bottleneck is.

---

