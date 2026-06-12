---
title: "Internet in guest Ubuntu 9.10 on VMWare (direct internet connection)"
date: 2010-03-01
forum: Virtualisation
---

### Post by pchayka on 2010-03-01
I have Windows7 as host system and VMWare workstation with Ubuntu 9.10 Desktop on it. Everything's fine, but internet connection does not work on guest OS. 

I have 2 LAN-connections - direct connection to internet (real IP address, like web-server) and VMware Network Adapter VMnet8, which is being automaticly installed. Connection type in VMware is NAT, Ubuntu has default eth0 (DHCP) connection. Few screens:


[IMG]http://img693.imageshack.us/img693/4236/firste.jpg[/IMG]

Sorry for russian version, but u've got the point :)

[IMG]http://img94.imageshack.us/img94/416/secondcc.jpg[/IMG]

Ubuntu's config.

I've tried all possible connection options for VMWare, but that didn't help. How to get internet work ?

---

### Post by dcstar on 2010-03-01
> **pchayka said:**
> I have Windows7 as host system and VMWare workstation with Ubuntu 9.10 Desktop on it. Everything's fine, but internet connection does not work on guest OS. 

I have 2 LAN-connections - direct connection to internet (real IP address, like web-server) and VMware Network Adapter VMnet8, which is being automaticly installed. Connection type in VMware is NAT, Ubuntu has default eth0 (DHCP) connection. Few screens:
.........
I've tried all possible connection options for VMWare, but that didn't help. How to get internet work ?

Try Bridging for the VM, as long as you have a DHCP server it will get allocated an IP address from your network.

The problem may be in the security settings on your Windows host.

---

