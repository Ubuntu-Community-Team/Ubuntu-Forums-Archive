---
title: "Alternative to virtualbox"
date: 2013-11-09
forum: Virtualisation
---

### Post by adriqn on 2013-11-09
I am comfortable using virtualbox managed with phpvirtualbox on a 12.04 headless server but the latest version of zentyal appears to have issues with the samba module when run as a guest OS in VB.  I have considered ESXi but there is no web based or linux based GUI for management plus nic bonding and APC UPS management looked problematic. 
My host network set up is as follows:
LAN bond0 with eth0, eth1 & eth2 as slaves
WAN eth3

Guest network 
WAN eth0 bridged to eth3
LAN eth1 bridged to bond0

I briefly tried KVM sometime ago but really could not get to grips with the networking as it seemed to disable the host network when the a guest was running so I could no longer connect remotely to the host.

What alternatives are available with a nice webbased GUI?
Thanks.

---

### Post by TheFu on 2013-11-09
There are lost of virtualization backends that are separate from the front-ends.  libvirt is generally the tool that front-ends talk with and it supports lxc, kvm, qemu, xen, virtualbox, and esxi .... to different degrees.

As for managing networks, there is openvswitch and the built-in linux bridge utilities. I think on 10G networks, OVS is 10% more efficient than the normal linux bridge utils.  If you have lots of physical hosts and need to migrate networks with minimal downtime, OVS is what you want. Otherwise, if 10 seconds to move a VM between hosts is fine any you are on anything less than 10G network, then the built-in bridge is fine. I've never had any issue with either, provided I manually configured them.  The automatically created bridges seem to be flaky based on forum posts - when I was setting up my last VM host network, automatic bridges didn't exist.

I can't imagine any networking that a Linux host wouldn't handle - and if Linux can do it, then KVM can as well. The host networking is definitely NOT disabled with guests are used.

I consider a web interface to be a security liability and much prefer to use an ssh tunnel and virt-manager to control VM creation.  To start and stop, the CLI virsh works great from any client machine - though virt-manager will work too.  I prefer to only have ssh with keys and auto-blocked failures on my VM hosts.  I suppose there are other web-front-ends that use libvirt ... don't know - never looked.  My setups are less than 10 VM hosts ... not to complex.

---

