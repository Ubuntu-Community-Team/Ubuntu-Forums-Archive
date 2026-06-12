---
title: "bindgraph not creating graphs."
date: 2009-08-19
forum: Server Platforms
---

### Post by pot_roast on 2009-08-19
RRDtool 1.2.19
bindgraph 0.2

There is another thread on here from ages ago talking about unescaped colons causing rrdtool to not make the graph. It seems that bindgraph has been updates since then, but I am still unable to get it to create any graphs.

[Wed Aug 19 19:16:09 2009] [error] [client 192.168.1.12] Premature end of script headers: bindgraph.cgi, referer: [http://192.168.1.69/cgi-bin/bindgraph.cgi](http://192.168.1.69/cgi-bin/bindgraph.cgi)
[Wed Aug 19 19:16:09 2009] [error] [client 192.168.1.12] Premature end of script headers: bindgraph.cgi, referer: [http://192.168.1.69/cgi-bin/bindgraph.cgi](http://192.168.1.69/cgi-bin/bindgraph.cgi)
[Wed Aug 19 19:16:09 2009] [error] [client 192.168.1.12] Premature end of script headers: bindgraph.cgi, referer: [http://192.168.1.69/cgi-bin/bindgraph.cgi](http://192.168.1.69/cgi-bin/bindgraph.cgi)
[Wed Aug 19 19:16:09 2009] [error] [client 192.168.1.12] RRDs::last(/var/lib/bindgraph/bindgraph.rrd): opening '/var/lib/bindgraph/bindgraph.rrd': No such file or directory at /usr/lib/cgi-bin/bindgraph.cgi line 158., referer: [http://192.168.1.69/cgi-bin/bindgraph.cgi](http://192.168.1.69/cgi-bin/bindgraph.cgi)
[Wed Aug 19 19:16:09 2009] [error] [client 192.168.1.12] Premature end of script headers: bindgraph.cgi, referer: [http://192.168.1.69/cgi-bin/bindgraph.cgi](http://192.168.1.69/cgi-bin/bindgraph.cgi)

--
I know that it's not creating the RRDs, but I'm not sure where the exact problem is, and do not see RRD logging anything.

Has anybody resolved this with CURRENT versions? (Google searches bring up either unanswered posts, or references to OLD versions) 
Side note, is there a way to get RRD to log?

Thanks!

Edit: I am also running Jaunty, if it matters

---

