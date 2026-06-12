---
title: "Fedora 9 status as an OpenVZ template on Ubuntu 8.04"
date: 2008-11-09
forum: Virtualisation
---

### Post by c00l2sv on 2008-11-09
Hi,
I've got a problem setting up a container with fedora9 on a OpenVZ Ubuntu 8.04 server.

The problem is described here 
[http://forum.openvz.org/index.php?t=tree&th=6728&](http://forum.openvz.org/index.php?t=tree&th=6728&)

Although it is said that the bug shouldn't exist anymore, I couldn't set up a fedora 9 container on Ubuntu 8.04 OpenVZ server.

Any help would be appreciated!
Thank you.

---

### Post by c00l2sv on 2008-11-09
[http://pastebin.com/f5ecf9e9](http://pastebin.com/f5ecf9e9)

the problems can be found in this log.
When the container starts and we're setting manually the venet0's ip
we have the network.
But if we're restarting the CT, we get problems.
The server's eth0 goes down!

The bug actually means that the container switches off the HN's network interface!

---

