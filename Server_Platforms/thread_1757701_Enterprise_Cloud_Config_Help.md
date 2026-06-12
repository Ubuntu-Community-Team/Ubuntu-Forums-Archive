---
title: "Enterprise Cloud Config Help"
date: 2011-05-13
forum: Server Platforms
---

### Post by jeitzen on 2011-05-13
Hello all and thanks in advance.

I have been following a walk through on creating a private cloud.

I have Ubuntu (natty) installed on two machines (Physical).

On my CC, when I try to do the node discovery. I get an error after running the following command

$ sudo euca_conf --no-rsync --discover-nodes

This is the error


root@HH-CLOUD-CNTRL:~# sudo euca_conf --no-rsync --discover-nodes
Failed to resolve service 'HHCLUSTER node' of type '_eucalyptus._tcp' in domain 'local': Timeout reached
Failed to resolve service 'HHCLUSTER node' of type '_eucalyptus._tcp' in domain 'local': Timeout reached

INFO: We expect all nodes to have eucalyptus installed in //var/lib/eucalyptus/keys for key synchronization.
****



Any help is appreciated and thanks in advance.

---

