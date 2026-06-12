---
title: "Can not ping my VMs from external network"
date: 2015-04-09
forum: Ubuntu Cloud and Juju
---

### Post by naser2 on 2015-04-09
Hi, All

I have deployed OpenStack Juno cloud on single node, Ubuntu 14 LTS
All VMs are ok, running.  I can access to VMs through console.
From VM I can ping Internet servers, My External Network.
From External Server I can ping both router port.
From Nova-Compute  I can access to both VMs - ping, ssh

ip netns exec qrouter-<ID> ping   is OK

But I can not ssh or ping my VMs from External Server.\

I guess that problem is in my firewall but I can not locate it.


[ATTACH=CONFIG]261194[/ATTACH]

Thanks.

---

