---
title: "NFS share UID incorrect on nfs storage pool"
date: 2019-07-16
forum: Server Platforms
---

### Post by matthewacooper on 2019-07-16
HI

I am not sure if this is the place but I have this problem with NFS storage pools in LXD.

Quick info on the problem before I say where I am. I have set up an NFS mount and configured LXD to use that as a DIR storage pool. The container is created find but when you touch, vim a file inside the container the UID should be root but is nobody and on the host, the file has the UID of root (0).

Now my current position

I first posted this problem on the JUJU discourse ([https://discourse.jujucharms.com/t/lxc-with-nfs-storage-pool-fail-bootstrap-and-deploy/1654](https://discourse.jujucharms.com/t/lxc-with-nfs-storage-pool-fail-bootstrap-and-deploy/1654)) With some great help. This leads me to post the bug on the LXD git hub issue 
([https://github.com/lxc/lxd/issues/5962](https://github.com/lxc/lxd/issues/5962)) and Thank you Stéphane.

So now I have posted a bug report on launchpad.net ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1836707](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1836707)) and I have confirmed with my setup that this bug is in Ubuntu 19.04, 19.04, 19.10 and Centos 7.

As I am a bit new to this my question is

1. Can someone point me in the right direction to start debugging this bug?
2. Is this a stupid set up and be slow (There is a 10G connection between the boxes and not under much load)
3. who are the right people to push this bug too.

Thank you

Matthew

---

### Post by matthewacooper on 2019-07-16
To add

I am thinking the bug is not getting the map value to set the UID so it is using the host UID value.

Matthew

---

### Post by TheFu on 2019-07-26
Just because you can run LXD on CentOS, doesn't mean it is a good idea.  
LXD is a Canonical project, so launchpad is the place. Monitor the bug there and watch other LXD bugs there.

---

