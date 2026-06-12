---
title: "Round Robin Port Fowarding?"
date: 2009-11-08
forum: Server Platforms
---

### Post by kevin11951 on 2009-11-08
I don't have the money to be able to get a second ip, but I want to try load balancing on an apache server, and was wondering if its possible to do round robin on a port forwarding level?  

My router is based on ubuntu, so I should have total freedom with the internals unlike consumer routers.

-Kevin

---

### Post by Vegan on 2009-11-08
What you want is part of cloud computing. Google it and you will see its a bit of work to get up and running.

Better is a faster server.

---

### Post by yknivag on 2009-11-10
You could install "nginx" in front of the as many apache servers as you have and it will not only take care of the load balancing (on a weighted round robin basis) but also cache unchanging static content to reduce load.

It's in the repos and configuration is very straight forward.

---

