---
title: "Mail/Squid Cluster"
date: 2007-10-18
forum: Server Platforms
---

### Post by johng4 on 2007-10-18
I am looking to setup a 3 node cluster using Balance.  The Balance part does not appear to be hard, and even though the free version is a bit limited (not the free BalanceNG), it does exactly what I'm needing it to do.

The real issue is replication/synchronization of the data I want to serve in this setup.

I want this cluster to handle Amavisd-new, Squid, and Dansguardian primarily.  

Master Node: SantaMaria
Slave Nodes: Nina, Pinta

I want all of the data stored on SantaMaria because it has the most storage.  

As it stands I'm looking at either setting up LDAP with replication, or NFS shares on all nodes pointing data back to SantaMaria.

Any recommendations? How-tos?

---

### Post by tkharris on 2007-10-19
I vote for the NFS option.

[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

---

### Post by johng4 on 2007-10-19
The more I read into this issue the more I agree that NFS is the way to go... I guess I was half hoping for someone to slap me around and tell me to just setup the LDAP server.

I've been told though, that if I want to setup a postgresql cluster I would need to setup LDAP for it..  I'm not even sure I'm going to go that route yet, but it is something that has been in planning for a while now.

---

