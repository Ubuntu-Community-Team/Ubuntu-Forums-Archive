---
title: "squidGuard pegging CPU?"
date: 2008-02-02
forum: Server Platforms
---

### Post by newkirk on 2008-02-02
I've got Squid and squidGuard installed and configured on an ubuntu Gutsy system (server and gateway router), and have run into resource problems:  On an athlon900 box with 768mb ram, with NO traffic being handled by squid/squidGuard, I see squidGuard processes using up anywhere from 75% to 98% CPU resources on an almost constant basis.

top - 14:22:17 up 12:23,  5 users,  load average: 10.35, 7.62, 6.63
Tasks: 138 total,   4 running, 134 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.2%us, 76.5%sy,  0.0%ni,  0.0%id,  0.0%wa,  2.0%hi,  1.3%si,  0.0%st
Mem:    775540k total,   767484k used,     8056k free,     4584k buffers
Swap:  2265124k total,    34852k used,  2230272k free,   474348k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
12023 proxy     19   0  4308 2684  872 R 32.2  0.3   1:00.03 squidGuard                                                      
12025 proxy     19   0  4312 2688  872 R 31.2  0.3   0:44.31 squidGuard                                                      
12024 proxy     19   0  4308 2688  872 R 29.5  0.3   0:39.71 squidGuard    

Since I'm not (yet) even passing any traffic through squid+squidGuard, why the hell is it tanking my server??  I can absolutely confirm that there's no traffic hitting it, it's a gateway server here in my home and no browsers are running, no iptables redirect is pointing at it yet, etc.  It's not consistent, I'll see a single squidGuard process hit 98.5% cpu, then drop off of 'top' for a few seconds, then three of them as above totaling somewhere between 85% and 98%, then four at 23%-26% each, then one at 85% plus two at 5% each, etc. And it's not just at startup when it's getting itself organized, it's always.  Load levels are 9.00-12.00 with it running, 0.05-0.1 without.

Also, I noted that the squidGuard version in the ubuntu gutsy feed is V1.2.0, while 1.2.1 has been followed by 1.3 in the official 'latest stable squidGuard' as per squidguard.org.

j

---

### Post by HermanAB on 2008-02-02
It should calm down after it built its database.  That may take an hour or so though.

---

### Post by newkirk on 2008-02-03
> **HermanAB said:**
> It should calm down after it built its database.  That may take an hour or so though.
Wow - it can take that long?  I didn't realize it would need that kind of time.

OK, thanks.  I'll let it chew overnight and see where it stands come morning.

j

---

### Post by newkirk on 2008-02-03
Nope, 12 hours later it's still gobbling CPU resources, running close to 100%.

j

---

### Post by HermanAB on 2008-02-03
Here are some guides I wrote many moons ago: [http://aeronetworks.ca/squidguard-howto.html](http://aeronetworks.ca/squidguard-howto.html)
[http://aeronetworks.ca/willowbark-howto.html](http://aeronetworks.ca/willowbark-howto.html)

Note the comments about 'paint drying and flaking off' if you do a 'restart'...

---

### Post by newkirk on 2008-02-04
Bingo, found the problem.  It was a typo in the config file, one of several ACLs was pointing at an invalid path.  I kept tailing the log and never saw it, for the same reason that it kept endlessly using up all CPU: every time it hit that point apparently squidGuard would bail out, and squid would immediately restart it.  I never looked through enough of the logfile at one view to see the error, as reprocessing the valid parts filled a screenful.  It hadn't occurred to me that it would be endlessly restarting, until I noticed the size of the logfile.

Thanks for the advice and the howto links.  Helped me polish and improve my config, which led to discovering the error.

j

---

