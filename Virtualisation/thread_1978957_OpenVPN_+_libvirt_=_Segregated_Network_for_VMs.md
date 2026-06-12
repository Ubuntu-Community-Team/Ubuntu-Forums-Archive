---
title: "OpenVPN + libvirt = Segregated Network for VMs"
date: 2012-05-12
forum: Virtualisation
---

### Post by teeks99 on 2012-05-12
I just setup an experiment, and I wanted to post about it here so that anyone interested in this could see it.

My goal was to create a network similar to the host-only networks where you can have VMs talk amongst themselves on their own network, except I wanted it to spread across multiple hypervisors. This was accomplished by running an OpenVPN client on each hypervisor, creating a new tap connection which I then could bridge VMs to, and presto the VMs were on the same network. To be clear, I didn't install OpenVPN on the VMs, just the hypervisors, the VMs thought they were just connecting to a normal ethernet network.

[http://teeks99.com/sys/OpenVPN-VMs/Tryout.html](http://teeks99.com/sys/OpenVPN-VMs/Tryout.html)

The major downside to this setup is that all traffic on the network goes through the OpenVPN server, making it fine for small networks like mine, but unpracticle for large or high-throughput networks. To solve this problem, I wrote up a proposal for a next step. If anyone has ideas towards this I'm all ears.

[http://teeks99.com/Ideas/P2P_VM_Network.html](http://teeks99.com/Ideas/P2P_VM_Network.html)

---

