---
title: "Writing technical system documentation"
date: 2007-02-01
forum: Server Platforms
---

### Post by nocturn on 2007-02-01
Hi all

Does anyone have some resources that are useful as an example/guide to write documentation of a system (in my case, a cluster).

What needs to be in there, how do you start this?

I'm good with technical things but writing something like this is a challenge...

Thanks

---

### Post by elst on 2007-02-02
I think that the best method depends on whether you're trying to compile data that describes the system (config settings etc.), or explain the practices and procedures that the humans should do.

In the first case, I'd recommend starting by using monitoring software to gather information, rather than falling into the trap of writing something that only describes a particular point in time, and will have to be constantly maintained to remain relevant.

For the second case, I'd suggest creating a Wiki and initially filling it with some categories and pages that seem useful. Then it's really easy to add to it incrementally as new things occur to you, and updating it is also so quick and easy that you can do it as part of your normal workflow. You can also easily restructure the information.

Big comprehensive documents can seem kind of impressive, but they are time-consuming to write, and if they aren't maintained then updating them again can be a chore. I've seen a professional tech writer estimate that to produce documentation to publication standard from scratch can take a total of eight man-hours or more per-page of drafting, fact-checking, proofing etc., and that chimes with my own experience. With a Wiki you can effectively invest the time in smaller installments.

I also suspect that larger documents also don't fit the way that many people use references anymore - it seems like plenty of people just go to straight to the section that's relevant at the time, rather than reading a technical reference from start to finish. A Wiki or similar is automatically searchable.

Probably not what you had in mind, but hopefully useful.

---

