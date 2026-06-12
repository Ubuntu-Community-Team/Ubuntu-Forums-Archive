---
title: "Ubuntu 14.04-15.04 iSCSI Boot not working"
date: 2014-12-29
forum: Server Platforms
---

### Post by bill70 on 2014-12-29
Is anyone else having issues booting Ubuntu server from a iSCSI Server (Microsoft)?

I have a windows 2012 Server which is hosting my Storage, along with a number of other items for multiple environments (ESXi, HyperV) and I am trying my hardest to get KVM also running but it is the only platform that will not boot after initial install of the O/S. Once the O/S finishes installing to the iSCSI device its discovered after logging into my iSCSI server, I reboot and it gives a number of NIC errors (There are 3 ports in the system, (2) Intel 1GbE and a 10GbE Mellanox). Only em1 has been configured and it is what is being used to logon to the iSCSI also. it ll works and the system sees the iSCSI device and installs to it, and then goes out and gets all the updates from the repo's but once it boots no-mas! puts me to a prompt that is not able to do anything! I cant even look at the interfaces file to see it unless I do a recovery boot and even then after adding in the additional interfaces (em2, and p55p1) nothing! These nodes have no internal storage so I really need this to work! 

Anyone?

---

### Post by bill70 on 2015-01-04
Can no one assist???

---

