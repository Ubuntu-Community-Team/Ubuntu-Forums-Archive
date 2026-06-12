---
title: "KVM and networking"
date: 2012-01-02
forum: Virtualisation
---

### Post by Erik-NA on 2012-01-02
I am a newbie to KVM, have some years of experience from vmware server. I am planning to migrate a firewall from vmware server to KVM.

I am trying to understand how to set up networking and KVM. I have some problems to solve.

[LIST=1]
[*]How to setup a bridge to a physical NIC (External ISP) where the virtual instance is a DHCP client getting the IP-adress via the NIC? The host should not have any IP-connection at all via the physical NIC. How should etc/network/interfaces look like?
[*]How to setup a bridge to a physical NIC (Internal) where the virtual instance is the DHCP server and the host is DHCP client? How should etc/network/interfaces look like?
[/LIST]

---

