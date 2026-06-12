---
title: "How do I set specific samba share sizes?"
date: 2013-07-04
forum: Server Platforms
---

### Post by brent1975 on 2013-07-04
Hello, I have been running a Ubuntu server for a couple years now and pretty much got it masters (for what I need it to do)  However, I have come to a point where I want to change up my shares that I have on the server with size limits. Example - Documents 1.5 gig, iso's 500 gig, so on. Currently all the shares have the same  allocation size. I use this at work as a local store for all my stuff I need. I don't suppose this is something that you can just configure without having to create separate partitions to the size I want and share them out?   Crossing Fingers  XXXXX

Thank you in advance

-Brent**&#8203;**

---

### Post by nerdtron on 2013-07-04
Seems really complicated. And I do think that partitioning is the only way here. You create a partition you want to share, mount it and then add a samba share.
Or maybe some experts on samba sharing can shed light on this :)

---

