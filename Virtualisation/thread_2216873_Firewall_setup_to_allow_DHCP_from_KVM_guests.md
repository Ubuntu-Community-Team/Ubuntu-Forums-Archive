---
title: "Firewall setup to allow DHCP from KVM guests ?"
date: 2014-04-14
forum: Virtualisation
---

### Post by Romu on 2014-04-14
Hi folks.
I'm setting up a virtualization server. The host is Ubuntu Server 14.04 + XFCE for some facilities + KVM.

I've setup a network bridge for my VMs and eveything works fine...except there is no way for the VMs to get a DHCP lease. I've added DHCP in ufw (67/udp IN and 68/udp OUT...or the opposite, don't remember, I just used the pre-configured DHCP rules), and no way to get the lease.

I'm sure this comes from ufw, because right now, ufw is disabled and VMs get their IP address without any trouble.

Any idea about the right ufw setup?

Thanks.

---

