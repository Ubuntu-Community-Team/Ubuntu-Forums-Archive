---
title: "LTS 6.06.2 not recognizing hardware correctly"
date: 2008-02-08
forum: Server Platforms
---

### Post by lnx4me on 2008-02-08
I downloaded the LTS server 6.06.2 to use on systems. previously 6.06.1 worked just fine with the exact same hardware meaning I installed .2 on the same system that .1 was on. I first did a complete install and setup of 6.06.1 the network cards came up eth1, ath0, eth0. all the software worked and works fine. then I booted to the .2 installer and did a complete install overwriting and setting it up just like it was a new system. during the install ath0 and eth0 showed up but no eth1 and then finally once the system booted I did an lspci and all the network cards where there. after configuring them in interfaces I rebooted the system. I then did an ifconfig ath0 eth1 and got error fetching device. the other odd thing was the interfaces eth1 and eth0 switched places. on .1 eth1 was the internet connected card .2 it became eth0. any ideas about what may be going on?
I put .1 back on and it is currently running just fine. :confused:

---

