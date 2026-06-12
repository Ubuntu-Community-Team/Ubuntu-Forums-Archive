---
title: "an idea about wiring mid sized networks."
date: 2012-03-22
forum: The Cafe
---

### Post by boblizar on 2012-03-22
i like the idea of a data center for a complex that would have several buildings.  like a school

have cluster, and give each node a 10gb/s fiber card  then runlines all over the place.  on the other end of the line, have a ubuntu node, set to proxy traffic, and reduce load.  have the cluster serve tons of OSPF stuff from quagga.

then have the linux node on the other end connect to a switch, and then run raceway conduit to boxes with 4 rj-45 ports. and if i needed more ports on one i could add more switches.

for the end user this is a good idea, because you can start small, 1 node in the data center, 1 node.  run more optical cable in conduit like sprinkling.  making sure to not make sharp bends.

fiber is good for long distance runs.  you can even get little boxes that convert fiber to rj-45, but im not exactly sure how the ip addressing would work on that.  (id have to figure it out at the time.)

---

