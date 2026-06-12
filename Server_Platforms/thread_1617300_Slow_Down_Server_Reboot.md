---
title: "Slow Down Server Reboot"
date: 2010-11-09
forum: Server Platforms
---

### Post by darrenm on 2010-11-09
Hi all.

I have a Lucid cluster running 2 nodes using Pacemaker/Corosync from the HA-Maintainers repo.

I have lots of resources on there including about 8 DRBD resources.

When I reboot the server it doesn't give it enough time to stop the stacked resources and properly demote / promote before rebooting the server.

Is there anywhere in the init shutdown sequence where I could make it hang, or wait for the corosync process to finish properly before timing it out and forcibly killing it?

Thanks.
Darren

---

