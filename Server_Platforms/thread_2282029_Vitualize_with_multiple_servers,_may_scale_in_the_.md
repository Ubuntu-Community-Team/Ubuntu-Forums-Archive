---
title: "Vitualize with multiple servers, may scale in the future"
date: 2015-06-11
forum: Server Platforms
---

### Post by Pazau on 2015-06-11
Hi all,

I am doing an experiment where I need to be able to virtualize a machine, and it must be able to use all the CPUs and RAM from all connected computers, all running the same version of Ubuntu server trough a network.

For the experiment, I have three desktops:

One, which have two NIC's.
Two, which have one NIC.

Either the virtual machine can be managed from any computer, or it must be administered from a master computer. It is not so relevant.

I've searched a bit for a few days and tried different setups:

1. High-Performance-Cluster for which the master computer has two NIC's. The one NIC connecting to the ordinary network, the second connects to all of the nodes through a switch. All nodes have only one NIC. As I understand, this is best practise when utilizing MAAS, or is there something I overlooked?

2. Redundancy-Cluster, where all the nodes and the master is connected to the same network. I can connect to them all through SSH, but I'm not sure whether MAAS will work if it don't manage DHCP and DNS.

It is also possible to completely run without MAAS, and put all the servers up individually.

But what is best practice?

---

### Post by TheFu on 2015-06-11
The HostOS always needs "some" CPU and "some" RAM that cannot be used by the guest VMs. The best practice depends on the amount of RAM and number of cores involved inside the physical hardware.

I always leave 512MB of RAM for the hostOS and 1 vCPU core on 4 core or more systems.  On an 8-core and 32G system, that is minor for the performance gained. After all, the hostOS does need to manage the guests and that requires RAM and CPU.

There are projects trying to create a minimal hostOS just for the purpose of providing enough OS to run VMs and/or containers and nothing more.  If you need something "proven", check out proxmox which is uses KVM and openvz.

If you don't need full virtualization (which currently is the only real way to have security), then using LXC or Docker containers is something worth looking into. Very little overheard happens with containers and I'd guess about 3 more yrs of work will be needed to nail down the security sufficiently for use outside development and test purposes. No way would I put any service running in a container on the internet today.

---

