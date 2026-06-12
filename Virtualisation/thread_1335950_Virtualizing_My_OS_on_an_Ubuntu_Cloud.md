---
title: "Virtualizing My OS on an Ubuntu Cloud"
date: 2009-11-24
forum: Virtualisation
---

### Post by Brindle7211 on 2009-11-24
Before I get into my detail about my question and setup I hope that this in the correct area to be posting this in. In Short I would like to Virtualize a Windows OS and an Ubuntu Desktop OS on top of an Ubuntu Cloud.

The Questions:
- Is a virtualized OS going to be bound to a single node and or processor core in my could?
- Would Cluster Computing be a more viable option as opposed to creating a private cloud for myself?
- What storage solutions would you recommend for such a setup, a cluster file system, or a single file server with a usable raid offering a few TBs of available disk space?

The Hardware:
Box 1: My Current server, and the only one I really use on a daily basis.
Intel Core 2 Duo 2.2 Ghz & 2GB of Ram
120GB OS HDD + Raid 5 w/ 3 250GB drives for critical data backup
Dual 100Mbit Nic's (I've setup my server as the router for my home network - It kicks the ***** out of my old linksys router)
Box 2: Intel Celeron 2.9 Ghz single core
JBOD raid created through LVM - 20GB for OS and 470GB available storage (it's not redundant and I plan on reworking the LVM)
Dual 100Mbit Nic's
Box 3: AMD Athon XP 1.8 Ghz
300GB of available HDDs
Dual 100mbit Nic's as well on this one too.

The Reasoning Before I get hammered:
I'm very interested in cloud and or cluster computing and would like to achieve a working setup, although with my hardware it certainly wouldn't be optimal imho based on the research I've done so far. After learining how to acheive my ideal, by way of proof of concept if you will, I plan on building "real" servers and clustering them together with the goal of virtualizing my desktop on them as well as a webserver, and possibly my brother's desktop too so we'd all be able to "share" the avaialble computing power of the server's in the cloud/cluster.

I will admit now that while I am noob imo, with only about 1-2 years of linux experience. Also if I might add data redundancy is of little concern at this time because I have a 3 1TB Raid 5 in my desktop that houses all my movies, music, pics, etc.

I appreciate anybody's input, and I thank the community in advance for their help as well! Cheers!

---

