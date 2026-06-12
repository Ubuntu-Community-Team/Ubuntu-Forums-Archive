---
title: "UEC // Cluster and Instance Failover"
date: 2010-07-16
forum: Virtualisation
---

### Post by minitiss on 2010-07-16
I've just installed the Ubuntu Enterprise Cloud and connected two nodes. It seems to work fine, however I've have a couple of questions that I hoped you're able to answer for me.

When I installed a new instance they all get installed on the node1, UEC does not balance the load onto the separate nodes. It is possible to configure so that the new instance gets installed on the node with fewest instances?

I also wonder if it's possible to setup failover on instances if node1 crashes. I've tried to disconnect the network from node1, but I'm unable to connect to the instances as it doesn't seem to failover to the other node. Isn't that the idea of a cloud service that it should automatically failover?

Regards,
Tom

---

