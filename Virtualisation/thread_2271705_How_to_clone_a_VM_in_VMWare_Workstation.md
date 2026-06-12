---
title: "How to clone a VM in VMWare Workstation ?"
date: 2015-04-01
forum: Virtualisation
---

### Post by arunkumargoge on 2015-04-01
I'm trying to setup openstack cloud in Ubuntu server 14.04 using VMWare workstation. I installed a ubuntu server say VM1 and updated it and everythings fine till now. When i clone the same VM say VM2. Do i need to change anything like mac id, host name? 
What are things i need to change when i clone a VM?

---

### Post by TheFu on 2015-04-02
Doesn't openstack require at least 3 physical machines to begin and 10 to make it useful for learning?
I've heard of devstack using a single physical machine, but that is for python developers to work on the code used by openstack.

Not saying you can't do what you want, just that I've never heard about this.

The Ubuntu instructions for juju/MaaS deployments assume 10 physical systems.

I've been looking for ways to my my 5 systems useful as a tiny private cloud too. Running KVM + libvirt is the easiest, but it doesn't address the as-a-cloud management which would scale to 10,000 physical machine deployments.  Proxmox might, but it isn't the darling of the "cloud" world like the highly complicated openstack group of tools are.  A few friends are trying to migrate their current openstack deployments (2k phy) to the next production release. I hear them cussing all the time. No good migration exists.

Sorry - I'm no help.  Is there any help on youtube?

---

