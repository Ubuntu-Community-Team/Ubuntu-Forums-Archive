---
title: "How do I make the server NOT cache disk blocks?"
date: 2011-01-04
forum: Server Platforms
---

### Post by Invader Amoto on 2011-01-04
I have an issue with a server that is running some programs that go up and down in terms of memory usage.
The server is also using ram to cache disk blocks, and it will use up almost all of the remaining ram doing so.
When memory usage spikes in the programs running, it runs out ram and has to remove the cache or use the swap file. This causes a LOT of problems with the programs that are running. They slow down, and eventually crash.
For example, 'free' will output that only half the system's memory is being used when I first start up the server. After a while, 'free' will show that 90%+ is being used, and "cached" shows up as using a lot of memory. The programs running on the server aren't even using up 50% of the server's memory.

Is there some way I can change how the server caches disk blocks or make it stop doing that altogether?

EDIT: Didn't even think to include some info about the server. 10.04 LTS 32 bit, running on 2 GB of ram with a 90 MB swap file.

---

### Post by psusi on 2011-01-04
You can't, nor do you want to.  Only ram that otherwise would be free is used for cache, and is given up as soon as a program needs it.  You can consider cache to be free, which is why the free program prints a line with +/- cache.

---

