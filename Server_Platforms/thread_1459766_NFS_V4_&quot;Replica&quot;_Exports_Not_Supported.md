---
title: "NFS V4 &quot;Replica&quot; Exports Not Supported?"
date: 2010-04-21
forum: Server Platforms
---

### Post by Automaton111 on 2010-04-21
All machines involved are 9.10 Server 64-bit.

[https://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.commadmn/doc/commadmndita/nfs_replicas_softmount.htm](https://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.commadmn/doc/commadmndita/nfs_replicas_softmount.htm) has a great description. NFSv4 is capable of auto failover to a   secondary server for NFS mounts that die on you.

I followed these instructions [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto) but I didn't use the "export" file system that they set up.

This is my Export on the primary NFS server (There's no space in the word "replicas."  The forum software is just showing one.)
> /home  192.168.0.0/24(rw,fsid=0,insecure,no_subtree_check,async,replicas=/home@msdevnfs1:/home@msdevnfs2)Here  is the fstab from the client server:
> msdevnfs1:/     /home   nfs4    _netdev,auto    0        0Everything mounts fine.  But when I stop the nfs-kernel-server  on the primary NFS server, no failover occurs on the client.  If i do an  ls, it just hangs.  It's supposed to failover to the replica defined in  the export!!!

---

### Post by Automaton111 on 2010-04-22
Bump :popcorn:

---

