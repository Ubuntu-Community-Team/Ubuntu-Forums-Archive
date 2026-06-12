---
title: "UEC platform idea"
date: 2011-07-30
forum: Ubuntu Cloud and Juju
---

### Post by TCA on 2011-07-30
I have been testing UEC and have an idea for a web hosting cloud.
This is what I have so far:
1. UEC,HDFS,Puppet w/ Git for the physical servers.
2. Ubuntu server with Puppet client for config man and provisioning running in a VM.

All storage will be from HDFS and will be accessible from each VM.
I will be purchasing a couple new servers when I get back to the states due to Virtualbox not supporting virtualization. I have been able to get UEC running in two VMs but can't start an image yet due to VB.

One of my goals is if a site starts to get a lot of traffic we can start a load balancer for it and have UEC auto spawn more images that will auto provision for the specific site and register with the load balancer.

Is this a plausible idea? I have only been able to get so far due to lack of hardware, any ideas/input you may have will be much appreciated.

---

### Post by kim0 on 2011-07-30
HDFS as in hadoop fs ? you might want to checkout gluster which recently released integration code with openstack (base for next ubuntu cloud)

---

