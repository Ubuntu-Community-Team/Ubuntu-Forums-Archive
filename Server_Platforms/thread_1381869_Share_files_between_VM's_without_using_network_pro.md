---
title: "Share files between VM's without using network protocol"
date: 2010-01-15
forum: Server Platforms
---

### Post by volkswagner on 2010-01-15
Hi,

I am trying to accomplish sharing files between various operating systems.

There are so many VirtualMachine server choices.

I am finding it difficult to word my query, to find an answer.

QUESTION:  Can I have one physical server running a VM server, either bare metal or with a host OS to do the following?
    Allow the Guest VM's share either a folder or partition on the host machine?  From what I have read, sharing a partition between guest and host may result in data corruption.  I am not sure about between guests.  

If I set up shares between guest VM's does the access have to go via a network?  IE: does the traffic go from the host NIC, to the router and Back?

From what I have read, high performance VM architecture implements a SAN storage for fast access.  At this time we don't have the investment capital to install a SAN and related high bandwidth network hardware.

I guess the main two questions are:

[LIST=1]
[*]How can VM's access shared files as if it was a local drive, vs. a network share?
[*]Do guest VM share access have to be routed, or is it handled internally?
[/LIST]

I hope this makes a little sense.

---

### Post by Lars Noodén on 2010-01-15
First option might be for the host to serve up NFS, SMB or AFS for the guests to use.  

If you run the guests one at a time, then you can always mount a regular partition directly in the guest.  I'm not sure what would happen if you tried to run more than one at the same time.

---

### Post by Fire_Chief on 2010-01-15
Virtualbox supports Shared folders between the host and guest VMs. It does not use network connections to do this but instead uses the VBox extensions installed on the guest VM to facilitate communication with the host for the folder share.

---

### Post by spynappels on 2010-01-15
If you use a bare metal hypervisor such as VMWare ESXi, it will have a virtual switch as part of the hypervisor. Each VM will have its own IP address, so you can use normal network protocols to send data between them, without going anywhere near the router. 

Also, I'm not sure whether it would work, but you could try setting one of the VMs up as a NAS box and use it for a shared storage solution.

---

### Post by volkswagner on 2010-01-15
> **spynappels said:**
> If you use a bare metal hypervisor such as VMWare ESXi, it will have a virtual switch as part of the hypervisor. Each VM will have its own IP address, so you can use normal network protocols to send data between them, without going anywhere near the router. 

Also, I'm not sure whether it would work, but you could try setting one of the VMs up as a NAS box and use it for a shared storage solution.

OK, perhaps I shall clarify a little if I may.  I am trying to run applications and query databases as if they are on a local disk.  If I use the virtual switch or run a VM NAS, what will my throughput be limited to?  I would like if the disk speed would be the bottleneck.

In general is having the VM's on one machine going to decrease query speed vs. running the query between to hosts on a Gigabit LAN or 10/100 LAN?

---

### Post by spynappels on 2010-01-15
> **volkswagner said:**
> OK, perhaps I shall clarify a little if I may.  I am trying to run applications and query databases as if they are on a local disk.  If I use the virtual switch or run a VM NAS, what will my throughput be limited to?  I would like if the disk speed would be the bottleneck.

In general is having the VM's on one machine going to decrease query speed vs. running the query between to hosts on a Gigabit LAN or 10/100 LAN?

Running a query to a MySQL server on another machine will always include some delay. Running it from one VM to another will be broadly the same as running it through any other Gigabit switch theoretically, but obviously the quality of hardware differs and the Virtual switch is a software solution. From experience, I've never seen much of a performance hit with the VMWare Virtual Switch in production systems. I've never worked with other virtualisation products.

I think the answer to your last question depends on the quality of your networking hardware and the spec of your VM host, but I have never noticed much difference between the two.

---

