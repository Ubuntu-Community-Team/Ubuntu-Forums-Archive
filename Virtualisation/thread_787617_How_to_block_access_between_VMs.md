---
title: "How to block access between VMs?"
date: 2008-05-09
forum: Virtualisation
---

### Post by m.brinkers on 2008-05-09
Any tips on how to give each virtual machine in a multiple virtual machine setup it's own subnet?

I would like to setup multiple virtual machines on one host using KVM. I have created a bridge on the host which each guest VM is using for it's network access. With this setup each VM uses the same subnet (ie the subnet of the bridge). Because I would like to regulate access between the VM's I would like to give each VM it's own subnet and route all traffic through an external firewall so this firewall can regulate all access.
Is it possible to create multiple subnets and have each VM use it's own subnet?

What do you recommend or use yourself to regulate access between individual VMs?

Should I install a firewall on each VM or is there a better solution?

Thanks,

Martijn Brinkers

---

