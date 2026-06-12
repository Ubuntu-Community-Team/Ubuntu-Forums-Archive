---
title: "Clustering mail servers"
date: 2007-04-27
forum: Server Platforms
---

### Post by apoth on 2007-04-27
I'm investigating a locally redundant mail server. If I've got three Ubuntu boxes and I want to run a single mail server over them, such that if any one of the three goes down the other two stay up, what would I need? Is it relatively easy to cluster them? Can you add new nodes on the fly?

Is there a simpler hack like running separate mail servers on a shared filesystem with network traffic diverted to one machine or the other? What about Gluster? Is Ubuntu not really suitable for this and if so are there other recommendations, particularly for someone who prefers apt over yum, etc?

Thanks

---

### Post by rsermilik on 2007-04-27
Take a look at [www.postfix.org](www.postfix.org)
There you can find links to your problem.
Of course you then have to run postfix but since this is a better choice its no problem :)

---

### Post by WesRatcliff on 2007-04-27
Here's some more food for thought...

[http://shupp.org/maps/ispcluster.html](http://shupp.org/maps/ispcluster.html)

It's a big endeavor that you can make VERY complex if you want to. :)

Wes

> **apoth said:**
> I'm investigating a locally redundant mail server. If I've got three Ubuntu boxes and I want to run a single mail server over them, such that if any one of the three goes down the other two stay up, what would I need? Is it relatively easy to cluster them? Can you add new nodes on the fly?

Is there a simpler hack like running separate mail servers on a shared filesystem with network traffic diverted to one machine or the other? What about Gluster? Is Ubuntu not really suitable for this and if so are there other recommendations, particularly for someone who prefers apt over yum, etc?

Thanks

---

