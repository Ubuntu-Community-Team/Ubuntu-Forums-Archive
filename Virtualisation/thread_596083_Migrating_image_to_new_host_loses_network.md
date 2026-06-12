---
title: "Migrating image to new host loses network"
date: 2007-10-29
forum: Virtualisation
---

### Post by Jolly.Tall on 2007-10-29
I have set up Ubuntu servers version 6.06, 7.04 and 7.10 on VM Server 1.0.4 on a WinXP host, and all work perfectly on their original host. But as soon as I try to copy the guest image to a new host I lose eth0 and hence network access. If I try to restart the network I get the following error:

'SIOCSIFADDR: No such device' and 'eth0: ERROR while getting interface flags: No such device'.

There is no such issue with a Centos 5 server, so I'm guessing this is an Ubuntu/Debian issue. I've asked on the VMware forums, and no-one seems to know the answer. It looks like it is not possible to migrate Ubuntu guests between VM servers, which is almost unbelievable. 

Does anyone have any ideas? Please.

---

