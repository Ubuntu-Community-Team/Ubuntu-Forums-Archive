---
title: "Need advice on a suitable Layer 2 Application for Ubuntu Server"
date: 2018-08-08
forum: Server Platforms
---

### Post by jdarby1983 on 2018-08-08
I'm currently designing a new network for a customer and during the lab phase I plan on having a Ubuntu server installed in the virtual "Site A" and also in the virtual "Site B"

The connectivity between them i will exclude from this discussion, but essentially i am wanting to know of an application I can install on each server and cluster/pair the app's together, the apps must require same network (same layer 2 vlan) connectivity.

Would anyone have any suggestions?

---

### Post by volkswagner on 2018-08-11
Additional information may help get the ball rolling. Leaving out the layer2 link may cause some to think this may be a road block if it's across the internet.

What applications be are you planning to "cluster/team"?  Why do you want two separate servers running the same app? Is it for failover, high availability, load balancing?

---

