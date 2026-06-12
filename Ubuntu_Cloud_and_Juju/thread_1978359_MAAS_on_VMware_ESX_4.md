---
title: "MAAS on VMware ESX 4"
date: 2012-05-11
forum: Ubuntu Cloud and Juju
---

### Post by amarcionek on 2012-05-11
I would like to run a 3 node MAAS on one of my ESX servers, mainly for software development purposes against OpenStack.

I was installing MAAS. I have one main server running the MAAS. I then added two nodes and the nodes shutdown themselves. I then clicked Accept and Commission.

[https://wiki.ubuntu.com/ServerTeam/MAAS/AddNodes](https://wiki.ubuntu.com/ServerTeam/MAAS/AddNodes)

I then manually powered on the two nodes in vSphere. However, the two nodes won't PXE boot.  I'm fairly certain that VMs can PXE boot, but I can't tell why they aren't working. Of course, maybe this is not even a supported configuration. I'm also no expert on how PXE boot works.

Finally, I tried to run "ubuntu-import-isos" indicatd here: [https://wiki.ubuntu.com/ServerTeam/MAAS](https://wiki.ubuntu.com/ServerTeam/MAAS) But it says command not found.

I have a DHCP server in my environment, but I can't let MAAS take that over. I suppose what I could do is set up a new subnet just for this testing environment.

---

### Post by amarcionek on 2012-05-14
EDIT: So I isolated MAAS on its own network 10.10.10.X and this seemed to have fixed it. DON'T FORGET TO RUN sudo maas-import-isos!!!

---

