---
title: "KVM:  List IP addresses for active guests?"
date: 2013-10-15
forum: Virtualisation
---

### Post by 1clue on 2013-10-15
Hi,

Maybe I'm just missing it?

On KVM, is it possible to get a list of VMs with their IP addresses?

VMware ESXi has this, and I find it incredibly handy.

Thanks.

---

### Post by TheFu on 2013-10-15
KVM is just a provider. The actual IP address comes from inside each VM based on static config or DHCP. Just use normal network tools to create a list of IPs - at least if you have a bridge setup. I've never used a VM-specific NAT setup. Guess connecting to the console of each will be needed in that case.

Lots of ways to create a list
* arp --> ping
* zenmap scan the subnet
* nmap scan the subnet
probably 20 other tools/methods exist. These are all that come to mind.

It is possible to dump all the other information about every VM using libvirt.**  virsh dumpxml {vmname}**  It is just that IP addresses are not part of that data.

---

