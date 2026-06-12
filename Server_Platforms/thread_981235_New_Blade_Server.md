---
title: "New Blade Server"
date: 2008-11-13
forum: Server Platforms
---

### Post by toallpointswest on 2008-11-13
I have a new IBM blade server with two blades installed, my idea is to cluster the blades together in such a way as they share resources. Is this possible?

---

### Post by Vegan on 2008-11-13
I have not tried using Ubuntu for that configuration. I looked into it and it seems vendors have specialized versions Linux for blade systems in a shared configuration typical of high performance systems.

Check with you blade vendor to see if software is available for clustering.

:guitar:

---

### Post by PilotJLR on 2008-11-14
This is possible, but it is complex. Pooling all the resources into one is basically parallel computing - for example Beowulf clutsters. 

If you're new to parallel computing, then this will be a challenging project, as applications have to be purposely built for parallel computing.

If you are a developer and know about this, then check out Beowulf clusters, and that should be a good starting point.
[http://www.beowulf.org/](http://www.beowulf.org/)

An HA cluster, where services migrate from server to server but do not run on each node concurrently, is a lot more attainable. If that is what you want to do, that's a different story.

---

