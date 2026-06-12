---
title: "failover cluster"
date: 2020-05-07
forum: Virtualisation
---

### Post by ts01539720 on 2020-05-07
Hi there,

I am new to the linux OS.
I was wondering if Ubuntu / other linux can allow me to install server 2012/2016 VM in a failover cluster between 2 x servers without NAS/SAN as I would like to put the servers in different locations.
Could anyone please advise how to 
- create the failover cluster in both servers
- install server 2012/2016 VM

Thank you very much.

Regards,
SGS

---

### Post by ActionParsnip on 2020-05-08
Sure. Just bridge the connection so that you get a LAN based IP rather than the internal network that virtualisation can use.
If the systems are on the same piece of tin its not really a good idea but for the sake of experimentation it's fine. 
For ease of use I suggest VirtualBox

---

### Post by slickymaster on 2020-05-08
*Thread moved to **Virtualisation**.*

---

### Post by TheFu on 2020-05-08
This isn't a beginner question.  Actually, this is a 3rd year sr linux admin question.

However, the shortest way to accomplish it would be to setup a proxmox cluster, i suppose.  I would do it a completely different way and i wouldn't touch windows, but whatever.

virtualbox is a toy solution for server virtualization, imho.  Mostly, virtualbox is fine for desktop-on-desktop VMs if you are stuck using windows as the host OS.  With linux as the host, we have many better< more stable, more efficient, non-oracle, options.

If you need step-by-step instructions, I'd say you are way over the required skills necessary to accomplish this project.  Linux is extremely powerful AND flexible to fit all sorts of requirements.  There are 20 different kinds of clusters, dependent on the exaxt workload involved. The :everything: types are the worst sort.

---

