---
title: "UEC Node registration problem"
date: 2010-06-10
forum: Server Platforms
---

### Post by VDEL on 2010-06-10
I am having trouble registering the node controller. It is simply not detected when i try  "euca_conf --list-nodes", and when I run "euca-describe-availability-zones verbose" the list of instances appears with 000/000 on the "free/max" column. I have also tried to force it doing "euca_conf --register-node ", and although it says "done", nothing happens.
I am running a two machines topology (frontend: CLC, CC, WALRUS, SC. node: NC). I can ping succesfully from any of the machines to the other one, so I guess it is not a problem of the connection.
Does anyone happen to know could be going on here?

The whole configuration I am running is like this:
- Ubuntu Enterprise Cloud.
- As I said, 2 computers: frontend and node.
- networking system: MANAGED-NOVLAN
- Front end with 2 interfaces: 192.168.1.211 and 192.168.5.2
- Node with one interface connected directly with the frontend: 192.168.5.1. (already configured it as a bridge, following the ubuntu enterprise cloud guide).

Thank you for your help!

---

### Post by VDEL on 2010-06-10
For additional info:

- I cannot find neither the nc.log or the cc.log in the node or the frontend, respectively. The rest of the eucalyptus generated logs do appear.

- euca_conf --register-nodes "192.168.5.1" outputs as following:
----------
INFO: We expect all nodes to have eucalyptus installed in //var/lib/eucalyptus/keys for key synchronization
Warning: cannot file file node-cert.pem in //var/lib/eucalyptus/keys/
Warning: cannot file file cluster-cert.pem in //var/lib/eucalyptus/keys/
Warning: cannot file file node-pk.pem in //var/lib/eucalyptus/keys/
Warning: cannot file file cloud-cert.pem in //var/lib/eucalyptus/keys/

Trying rsync to sync keys with "192.168.5.1"... done.

----------
But in fact this four files are on the /var/lib/eucalyptus/keys of the node.


-I thought it might be a key synchronization problem, but looking in the /var/lib/eucalyptus/.ssh/authorized_keys of the Node I can see the RSA key.

---

