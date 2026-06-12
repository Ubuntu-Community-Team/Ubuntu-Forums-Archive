---
title: "Add vlans inside LXD."
date: 2018-03-20
forum: Server Platforms
---

### Post by tbispo on 2018-03-20
Hi

I have an LXD container running inside an Ubuntu 16. I would add some vlans inside that container and expose it to the other machines on the network.

But when I try to reach the container from a VM it does not work. Is there any configuration I can do to get around this problem.
Note. These vlans inside the container are created automatically by the system. There may be more than 30 vlans within this container.


LXD config

config:
  environment.http_proxy: ""
  user.network_mode: link-local
description: COS profile
devices:
  eth0:
    name: eth0
    nictype: bridged
    parent: br0
    type: nic
name: cos
used_by: []

---

### Post by darkod on 2018-03-20
Why vlans? I haven't worked with LXD but in any virtual environment it is usually very easy to create virtual switches. Then you can have multiple virtual NICs each connected to designed virtual switch which simulates traffic between VMs like they are on VLANs.

---

### Post by tbispo on 2018-03-21
I asked the client about this solution. But the client application uses the Vlan inside the container.

---

