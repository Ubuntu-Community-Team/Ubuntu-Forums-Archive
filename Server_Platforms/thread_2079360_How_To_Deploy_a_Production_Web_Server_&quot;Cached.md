---
title: "How To Deploy a Production Web Server &quot;Cached&quot; From a Secondary Server?"
date: 2012-11-01
forum: Server Platforms
---

### Post by Jaffray on 2012-11-01
Hello Ubuntu Forums!

I'm new here.  Names Peter Jaffray.

I would like to know what terminology I should be using, what searches I should be performing, etc. to accomplish the following task:

I would like to launch a server which copies cached copies of the websites from my main server.  I am reaching the point where my website traffic is becoming an issue and the load on the database is quite large.

Thank you :)

---

### Post by chadk5utc on 2012-11-02
I believe what your looking for is "Load balancing" I have not had reason for this so I have not personally tested it but found this link to get you started, hopefully. If possible I'd do some testing before installing this into a production server.
[http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster](http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster)

---

### Post by sandyd on 2012-11-02
> **Jaffray said:**
> Hello Ubuntu Forums!

I'm new here.  Names Peter Jaffray.

I would like to know what terminology I should be using, what searches I should be performing, etc. to accomplish the following task:

I would like to launch a server which copies cached copies of the websites from my main server.  I am reaching the point where my website traffic is becoming an issue and the load on the database is quite large.

Thank you :)

hmm
You probably want a http accelerator caching server like varnish or a reverse-proxy cacher like squid. I have generally found varnish to be the better one.

---

### Post by Jaffray on 2012-11-04
Thanks guys.  Load balancing is exactly right.  I looked into those options and while doing research I found mod_pagespeed which seems to really help as well. 

You can use mod_pagespeed to create static files which can then be moved and served from anywhere!  A new phrase I learned is "Sharding Domains".  But all in all its load balancing which is what I need.

---

