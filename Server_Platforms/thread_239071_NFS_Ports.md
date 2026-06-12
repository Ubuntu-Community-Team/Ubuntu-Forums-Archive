---
title: "NFS Ports"
date: 2006-08-18
forum: Server Platforms
---

### Post by hotpurple on 2006-08-18
Hi,

I'm having trouble with NFS. I have firestarter configured on my server (Dapper), and have selected to allow NFS connections through from my client machines. However, unless I disable the firewall I cannot connect the NFS clients. The acivity log says that I am attempting to reach ports all over the place from the client when I try to connect, eg, 684,681,920,917.

As I really need to be able to use NFS I have allowed these ports through, but is this normal?

Chris

---

### Post by lamego on 2006-08-18
Please read this thread to find the ports used by NFS:
[http://lists.netfilter.org/pipermail/netfilter/2005-January/058350.html](http://lists.netfilter.org/pipermail/netfilter/2005-January/058350.html)

---

