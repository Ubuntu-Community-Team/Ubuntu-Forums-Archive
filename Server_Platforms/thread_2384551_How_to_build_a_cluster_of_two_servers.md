---
title: "How to build a cluster of two servers"
date: 2018-02-08
forum: Server Platforms
---

### Post by dirk-lehmann on 2018-02-08
Hello,

I was wondering if somebody could and would let me know, or send me a documentation, how to build a cluster of two Ubuntu 16.04 LTS servers.

DL

---

### Post by darkod on 2018-02-08
Not all applications are clustered in the same way AFAIK. So if you can post more details about what actually you plan to cluster, someone can probably give you an advice...

---

### Post by LHammonds on 2018-02-08
Clustering is typically based on the application and is VERY specific per application.  Such as clustering for MySQL database servers or Apache web servers.  There typically isn't just one way to do a cluster either.  For example, there can be 3 different types of nodes in a [MySQL cluster]("https://en.wikipedia.org/wiki/MySQL_Cluster#Implementation").

Or are you talking about [Distributed Replicated Block Device]("https://help.ubuntu.com/lts/serverguide/drbd.html") which replicates file systems between servers?

Or are you talking about high-performance computing such as a [Beowulf cluster]("https://help.ubuntu.com/community/MpichCluster")?

LHammonds

---

### Post by dirk-lehmann on 2018-02-10
I would like to build a clustered hypervisor based on Ubuntu 16.04 LTS. At the moment I use single server with Oracle VirtualBox. Which Hypervisors can I decide between and are able to import my existing virtualbox virtual maschines without problem or trouble? I was wondering what cluster is easy and reliable to build with a second server for running the existing virtual maschines instead of running them on single server.

---

### Post by dirk-lehmann on 2018-02-10
Seems have to use KVM to do that. Is there a how to for Ubuntu 16.04 LTS available?

---

### Post by LHammonds on 2018-02-10
I have not implemented anything like this but below are the results from my google-fu.  I currently use VMware ESXi and will soon be switching to Nutanix Acropolis.

[ DRBD Pacemaker HA Cluster on Ubuntu 16.04 ](https://www.theurbanpenguin.com/drbd-pacemaker-ha-cluster-ubuntu-16-04/) (2016)
[Ubuntu 16.04 Live Migration](https://www.server-world.info/en/note?os=Ubuntu_16.04&p=kvm&f=6) (2016)
[Ubuntu KVM cluster question](https://serverfault.com/questions/90378/ubuntu-clustered-kvms) (2009)
[High-Availability KVM Virtualization on Ubuntu 12.04, 12.10, 13.04](http://linux.opm.si/programska-oprema/linux-gruca-cluster) (2008)

LHammonds

---

### Post by dirk-lehmann on 2018-02-10
If I going to install also Nutanix. With two physical machines it seems to me that I have to install for example Community Edition not as single-node cluster. But as multi-node cluster on each and let them discover automatically more or less, don't I?

---

### Post by LHammonds on 2018-02-11
I have not yet installed Nutanix so I couldn't say.  I was under the impression it had to have 3 nodes at a minimum.  I will be buying Nutanix hardware as well later this year.

LHammonds

---

