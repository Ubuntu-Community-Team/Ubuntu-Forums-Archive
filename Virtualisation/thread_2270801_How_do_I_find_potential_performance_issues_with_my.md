---
title: "How do I find potential performance issues with my Ubuntu VM?"
date: 2015-03-25
forum: Virtualisation
---

### Post by shahin on 2015-03-25
I have version 14.01 running in VMware workstation. Every time I ran Android Studio, which is a development environment tool, and a browser such as Chrome the VM slows down immensely. My question is how do I find out if the VM is running out of memory, cpu, or other resources? I did run top, and nothing stands out to me. Should I post to a more relevant group? I looked in the list, and there is not one dedicated to performance issues. Should I post I have the VM disk partitioned and how much I have allocated to each?

---

### Post by TheFu on 2015-03-26
Please post the VM specs and the HW specs for the real physical machine.
Also, you should realize that android development will be a dog on less than 4 vCPUs, 8G of RAM and fast storage. That is the nature of java. 

Running a VM is an exercise in sharing resources. 

If the VM takes all the resources from the physical host, it will perform badly.
If the host takes all the resources from a VM, it will perform badly.
If there are too many VMs running concurrently, most will perform badly.

The goal is to share resources across the host and all running VMs so that no performance impact is felt.  So .... I wrote a how-to for virtualbox, but it applies to VMware-Workstation too. [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) - take the general ideas and follow those. Pay close attention to the storage section, RAM and vCPUs - also - it is best to go with a lite desktop, not Unity or any desktop that wants 2D/3D graphics.

Lots of people post in this forum about performance issues "slow" is the keyword.

Why would the VM disk partitioning matter? Hopefully you have 2 - / and swap. Anything more for most VMs is wasted effort and large files belong on networked storage (NFS usually), not inside a VM. There are exceptions, but not many.

---

