---
title: "LXD 'private' subnet.."
date: 2016-10-20
forum: Virtualisation
---

### Post by chris-trash on 2016-10-20
Hi folks..


I've got a bit of stuff running in LXD fine using conventional bridged networking and the local lxd-bridge network and now I'd like to simulate a private subnet behind a linux router/firewall to do a POC for a project..


My google-foo has let me down on this one, so thought I'd post here as I've clearly missed something along the way. :-)


The setup so far..


16.04 lxd, br0 bridged to eth0.


I created another bridge just using "brctl addbr brt1" and then created a profile called 'bridge' with the following:
```

name: bridge
config: {}
description: ""
devices:
  eth0:
    nictype: bridged
    parent: br0
    type: nic
  eth1:
    nictype: bridged
    parent: brt1
    type: nic

```


And a profile called 'client' with the following:
```

name: clients
config: {}
description: ""
devices:
  eth0:
    nictype: bridged
    parent: brt1
    type: nic

```


Then creating some containers with:
```

lxc launch ubuntu:16.04 bridge -p bridge
lxc launch ubuntu:16.04 client1 -p clients

```

I then went into the containers and manually set IP's on the brt1 nics but they can't ping each other..  (Not worried about routing etc yet, if I can ping I can fix everything else. :) )

so lxc list gives:

```

+----------+---------+--------------------------------+------+------------+-----------+
|   NAME   |  STATE  |              IPV4              | IPV6 |    TYPE    | SNAPSHOTS |
+----------+---------+--------------------------------+------+------------+-----------+
| bridge   | RUNNING | 10.86.1.156 (eth0)             |      | PERSISTENT | 0         |
|          |         | 172.25.1.1 (eth1)              |      |            |           |
+----------+---------+--------------------------------+------+------------+-----------+
| client1  | RUNNING | 172.25.1.2 (eth0)              |      | PERSISTENT | 0         |
+----------+---------+--------------------------------+------+------------+-----------+
| client2  | RUNNING | 172.25.1.3 (eth0)              |      | PERSISTENT | 0         |
+----------+---------+--------------------------------+------+------------+-----------+

```

Going forward I want to put a DHCP server on 'bridge' that hands out addresses to client'x' as well, so I'm guessing some sort of promiscuous setting will be required as well, but again, if I can ping I'd be happy.

Anyone got a pointer in the right direction for this?

---

