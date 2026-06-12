---
title: "Help me setup Apache for high traffic"
date: 2006-02-13
forum: Server Platforms
---

### Post by trancephorm on 2006-02-13
My current (i think relevant) settings are these:

mpm-prefork mode,

Timeout 100
KeepAlive On
MaxKeepAliveRequests 500
KeepAliveTimeout 10

StartServers         20
MinSpareServers      20
MaxSpareServers      60
MaxClients          256
MaxRequestsPerChild  3000

The machine is really a good one: IBM eServer (Xeon 3 Ghz, 2 GB RAM), but the site it serves is pretty much high-traffic, I have really lot requests for on small file (about 200 bytes), and it seems I'm hitting the MaxClients limit (which is shown in error_log)... funny thing, resources are free, load is below 1, there are plenty of memory, processor does not go above 1%... so I think the problem is Apache's configuration.

Will compiling Apache to mpm-worker mode help? I doubt.

So please help me, how to raise limits.. It's urgent, site is in production phase.

Greetings,
Marko

---

### Post by phrozen on 2006-02-13
have you looked into [LightTPD]("http://www.lighttpd.net/")
before you say poo poo to it have a look, it was designed

the guy who wrote it was trying to make a server that could handle 10 thousand connections in parallel on one server, this is called the [C10K Problem]("http://www.kegel.com/c10k.html")

---

### Post by trancephorm on 2006-02-13
thanks, i was able to successfully setup lighttpd to work, but have some problems with /etc/init.d/lighttpd script which is not working on Ubuntu 5.1.. do you have some tips on that topic? :)

i hope lighttpd will solve my high-traffic related problems...

thanks..

---

### Post by trancephorm on 2006-02-14
it seems that lighttpd is handling connections much much better than apache 2.0.52, i tihnk my case is solved... thanks for a good advice!

---

