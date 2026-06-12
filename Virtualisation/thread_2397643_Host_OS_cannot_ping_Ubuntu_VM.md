---
title: "Host OS cannot ping Ubuntu VM"
date: 2018-08-01
forum: Virtualisation
---

### Post by jazeera on 2018-08-01
This has been asked several times on this forum but with varying degrees of twist. My host is Windows 7 64 bit and my VM is Ubuntu 64 bit as well. Defined two network adapters Bridged & Host-Only. DHCP is enabled on the virtual. I am able to access the internet on the VM but I can't ping the host nor can the host ping the VM. I have disabled firewalls on both the environments. 

When I look at my Network Connections, I do not see Bridged Network. All I see are the VirtualBox Host Only Network and my Wireless Connection to the router. I am connecting to the corporate network through VPN.

I tried NAT mode with Port Forwarding and had the same result. Bottomline I can access the internet from the VM and the host but can't communicate between the two environments.

What am I doing wrong?

Thanks

---

### Post by LHammonds on 2018-08-01
Is the gateway for the host and VM both pointed to the same IP?  And do they both have IP addresses on the same subnet that is configured on the bridged NIC?

---

