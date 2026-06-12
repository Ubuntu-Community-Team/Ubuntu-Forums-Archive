---
title: "Ubuntu 18.04 Can't add 4rth node to Gluster cluster."
date: 2019-11-21
forum: Server Platforms
---

### Post by pepsifx357 on 2019-11-21
I've having a strange problem.  I'm using gluster 3.13.2 and I've got 4 servers, node0, node1, node2, node3.  Each node is a KVM virtual machine that was cloned from node0 after installing glusterfs-server and adding a data directory in the home folder.  I changed the MAC addresses so they've all got different IP addresses from the DHCP server.  I've changed all of their hostname and hosts files to reflect this.  Everything, as far as networking goes, is correct and all nodes can ping the other nodes, using host names, with no problems.

When I run:

```
sudo gluster peer probe node1
```

All works like it's supposed to.

When I run:

```
sudo gluster peer probe node2
```

All works like it's supposed to.

When I run:

```
sudo gluster peer probe node3
```

It is successful, in that it adds node3 to node2 as an alternative name, as if it was the same server or something.

So when I detached all of the nodes and started over, now it says:

```
peer probe: failed: node3 is either already part of another cluster or having volumes configured
```

This isn't the first time this has happened.  I tried to create a cluster a year ago and ran into the very same problem.  I can add up to 3 servers to a pool, but as soon as I add a 4th server, it does this.  I can't seem to find anything on google that covers this particular issue.  Anyone here have any ideas?

---

### Post by pepsifx357 on 2019-11-21
I don't know what the problem was, but purging glusterfs-server on node3 and reinstalling it seems to have solved the problem.

---

