---
title: "Load blancing and Shared Memory in Apache WSGI Python script (mod_wsgi)"
date: 2012-08-15
forum: Server Platforms
---

### Post by dotchristopher on 2012-08-15
Hi All!

I've been looking into optimisation for a Python script which runs within Apache2's WSGI (mod_wsgi)- essentially trying to figure out the precise amount of memory associated with a particular request to a WSGI python script.

I've found the OpenBSD vmmap tool but for the love of $DEITY can't find the source anywhere online or within the bowels of a Mac. This looks like the program I need to discover what I'd like to know- does anyone please know if it can be obtained anywhere without needing to download the entire of OpenBSD!? 

Alternatively, does anyone know of any good methodology or tool included within Ubuntu/Debian (my test system) that will allow me say for certain that the memory is or isn't shared between the requests (which will give me a clearer picture of what can be achieved and how to best go about the load balancing [sorry, coding ninja, computer science daydreamer]). Using the Apache Benchmark tool 
ab, 10,000 requests with 1000 concurrent users takes approx 10s and uses somewhere between 500 and 1500Mb of RAM, depending on how I set the concurrency.

For those that are interested, the chain is:
Apache > Python (WSGI, importing several modules) > ApSolr > Tokyo
What I'd like to find out is how much (if any) of the python base libraries themselves or anything else loaded via import statements are being shared between each request, and whether there can be any optimisation between python and the solr/tt interfaces. The final  system (however I choose to split it up) will end up having to deal with  6+ figures over a 5-10 minute timeframe.
To cheat in the short term (get a handle on the load and requests per second) I simply duplicated the WSGI setup to two ports (two virtual hosts in the Apache config) and ran the test above on each port in parallel (at the same time). 
Answering approx 20,000 requests in around 14 secs seemed to take approx 3.5Gb of memory, leading me to believe that everything's simply being copied instead of reused!


Thanks in advance for your help. You'll notice this kind of system probably won't be given away for free, though I do plan to return a fairly substantial chunk to the OSS community (although Ubuntu might not end up a recipient).

---

