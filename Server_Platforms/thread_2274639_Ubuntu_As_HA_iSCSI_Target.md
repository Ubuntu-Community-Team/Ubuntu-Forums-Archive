---
title: "Ubuntu As HA iSCSI Target"
date: 2015-04-21
forum: Server Platforms
---

### Post by joebell on 2015-04-21
I am engaged with idea to create a highly available iSCSI targets with two Ubuntu Server 14.04.2 LTS boxes. My goal is it to connect the iSCSI targets to two Hyper-V nodes being in a Microsoft Failover Cluster, thus eliminating purchase of expensive commercial SAN devices. Searching the Internet I found it could be achieved with DRBD+Corosync+Pacemaker, but have not tried it before I dive into this technology a little bit deeper. Has somebody among you some experience with projects alike and help me find out suitable configuration? Is this a solution that could provide Cluster Shared Volumes to virtual machines running on Hyper-V serves and allowing them mobility throughout the cluster? 

Many thanks for any reaction I am anxious to see.

---

### Post by bapoumba on 2015-04-21
*Thread moved to **Server Platforms**.*

---

### Post by joebell on 2015-04-23
Hm,

It seems not to be a good idea :oops:. Did really nobody make some HA iSCSI target with DRBD+Corosync+Pacemaker from two Ubuntu Server 14.04.2 LTS 64-bit boxes? Will there bo no reaction at all? I would be glad to read any reply (negative or positive).

Thnx!

---

### Post by darkod on 2015-04-24
So far I have only tested a simple cluster but for a firewall gateway setup that had no data to sync between the nodes. It works good and you should have no problems setting it up. What you need to be careful about is the data sync in your case because if the secondary node needs to kick in it needs to have identical data with the primary.
Try setting up a test virtual environment and see how it goes. That's the only way to test and tune your setup. You can use something like virtual box or anything alike. If you need help with something specific in the setup post again.

---

### Post by joebell on 2015-04-28
Many thanks for this reply and drawing my attention to possible weak points of this configuration. I really do appreciate your comments.

---

