---
title: "multiple processor usage"
date: 2012-02-06
forum: Server Platforms
---

### Post by _Dan on 2012-02-06
Hey,

I guess this is a simple question, but it relates to servers... If I have a server with 4 processors, how intelligent is linux about distributing processes between the cores?

Say, I have 4 media serving daemons that are started on boot.

Will Linux have the sense to distribute them evenly?

And can a processes change core after being started? (because I notice through ps -AF that at the moment 3 of my 4 daemons are currently running on processor 0, with only one of them on another processor...)

---

