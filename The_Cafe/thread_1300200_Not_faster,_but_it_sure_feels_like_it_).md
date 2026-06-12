---
title: "Not faster, but it sure feels like it :)"
date: 2009-10-24
forum: The Cafe
---

### Post by The Real Dave on 2009-10-24
After reading an article in Linux Format, and complaining for a few days about my terrible internet speed, I decided to try installing squid proxy. Damn did it speed things up :) Didn't change my download speed of course, but it *feels* faster, and more usable. And it was so simple. Squid was in the repos, and after that, only two quick modifications were needed, i added ```
cache_dir ufs /home/dave/squid 500 16 256
``` to /etc/squid/squid.conf (just threw it to the end of the 5k :shock: line doc), and ran ```
chmod 777 /home/dave/squid
```.

All that was needed after that was to change the settings in Firefox to use the proxy localhost:3128 . And bam, my pages, after the first load, load faster. 

I hope to turn an old 451Mhz PIII I have lying around into a proxy for my network, so that everyone can benefit :)

Anyone else using a proxy to speed up their internet?

---

