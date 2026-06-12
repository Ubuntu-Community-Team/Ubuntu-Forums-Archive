---
title: "Can VM's use more than one node in Ubuntu Cloud?"
date: 2011-06-07
forum: Server Platforms
---

### Post by paulocoghi on 2011-06-07
Can a Virtual Machine, instantiated in the Ubuntu Cloud (UEC), use resources from more than one node?

---

### Post by Rusty au Lait on 2011-06-07
I assume your reference to 'resources on other nodes' is instances running on another node since the only things on any node are other running instances. If so, then yes, you can access other instances on other nodes from your instance but only if you make those other instances available to the network.

---

### Post by paulocoghi on 2011-06-07
Sorry. I wonder if the same virtual machine can allocate resources from different nodes.

An example, we have 5 hardware nodes with each 2x Quadcore. Can one VM use 20 cores? Or is 8 core max?

---

### Post by Rusty au Lait on 2011-06-07
Sorry. I'm not 100% but I believe the answer is no. That is more in the realm of Beowolf or another distributed computing structure.
Are the other resources you want to access more RAM, another core CPU? Or do you want more accessable processing threads?
Here's a link to a wiki article [http://en.wikipedia.org/wiki/Grid_computing](http://en.wikipedia.org/wiki/Grid_computing)
There are others.

---

### Post by paulocoghi on 2011-06-07
Thanks for the reply!

But, in this case I don't see the advantages of cloud. What is the reason to invest in a cloud solution if you don't get more as a dedicated server at the end?

---

### Post by paulocoghi on 2011-06-07
I want to enable provisioning of CPU and RAM to virtual machines instantied in the cloud.

For example, one VM is instantied with 4 cpu core and 4 GB RAM, and now I want to provide more 4 cpu cores and more 4 GB RAM, making the total resource used (8 cores and 8 GB RAM) greater than the resource of a single node (for example, 4 core and 4GB RAM).

Is it possible?

---

