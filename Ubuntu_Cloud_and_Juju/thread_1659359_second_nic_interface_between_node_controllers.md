---
title: "second nic interface between node controllers"
date: 2011-01-03
forum: Ubuntu Cloud and Juju
---

### Post by oldhoot on 2011-01-03
I want to add a second nic interface between my nodes, specifically a 10GE subnet.  The interfaces work at base level but not within the instances.  Is there a short course howto for adding more nets/bridges to the node controller vms?

---

### Post by kim0 on 2011-01-04
I think you probably want to "bond" the 2 NICs you have, then create the NC bridge on top of that bond

---

### Post by oldhoot on 2011-01-04
Not really.  My primary nic that I used to build the cloud is just a gigE.  The second nic is 10igigE and I want to use it for high bandwidth traffic.

---

### Post by kim0 on 2011-01-05
I am certain a NC cannot make use of multiple NICs for separating different network traffic (i.e management on eth0, VM traffic on eth1). Thus, if the NICs are of equal speeds, it makes sense to bond them. If not, as in your case, just use the 10G NIC alone I guess

---

