---
title: "help with virtual networks being auto-created"
date: 2024-05-21
forum: Virtualisation
---

### Post by coolmike8902 on 2024-05-21
I'm running Ubuntu 22.04. I was experimenting with Openstack on lxc and I have created a situation where virtualnetwork interfaces are being auto-created and I cannot figure out the source. If I run ip a it lists them, e.g: 

vnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master bridge2 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:f0:97:2a brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fef0:972a/64 scope link 
       valid_lft forever preferred_lft forever

and it's seriously messing up my networking. I tried deleting them using sudo ip link delete vnet1, but they just come back. The last thing I tried that probably did it was ansible, and I uninstalled that. I can't even figure out what is making them. Please help.

---

### Post by TheFu on 2024-05-21
Removing ansible won't undo anything.  Ansible does things only when run and those things are supposed to be omnipotent - meaning running once or 500 times shouldn't matter if the change is already applied.  If the config already does what the ansible playbook says, then no files should be touched.

Openstack is a separate skillset, so you might want to seek help on an openstack forum.  Few home users have any need for openstack.  Heck, I struggle to find a good reason to use Proxmox with clustering, though I've thought about it 50+ times since 2008.

I've never trusted automatic virtual networks. I want to create any bridges or links manually.  When I started doing VMs at home, the automatic VMs were terribly slow compared to the manually created ones, so I've just never stopped doing it manually.  Plus, I think the automatic ones are host-only or perhaps NAT, so they can't really be used outside the host the VM/Container is running on.

---

### Post by coolmike8902 on 2024-05-22
This is daunting. I have found these things:

 root        4694  0.0  0.0   9364  2888 ?        Ss   May21   0:45 bash /snap/microk8s/6809/apiservice-kickerroot        4710  0.0  0.0   9364  2892 ?        Ss   May21   0:00 bash /snap/microk8s/6809/run-cluster-agent-with-args
root        4711  6.7  0.0 5557616 62304 ?       Ssl  May21  78:15 /snap/microk8s/6809/bin/containerd --config /var/snap/microk8s/6809/args/containerd.toml --root /var/snap/microk8s/common/var/lib/containerd --state /var/snap/microk8s/common/run/containerd --address /var/snap/microk8s/common/run/containerd.sock
root        4783  2.2  0.1 1479512 240444 ?      Ssl  May21  25:43 /snap/microk8s/6809/bin/k8s-dqlite --storage-dir=/var/snap/microk8s/6809/var/kubernetes/backend/ --listen=unix:///var/snap/microk8s/6809/var/kubernetes/backend/kine.sock:12379

for example, but I have no idea how to stop them. They are not even listed as installed snaps.

---

