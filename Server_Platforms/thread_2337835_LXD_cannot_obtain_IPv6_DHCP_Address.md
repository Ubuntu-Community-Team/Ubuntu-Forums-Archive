---
title: "LXD cannot obtain IPv6 DHCP Address"
date: 2016-09-22
forum: Server Platforms
---

### Post by bdubn on 2016-09-22
I have installed LXD. After firing up my first container running Ubuntu 16.04, it obtains an IPv4 DHCP address by default. I am running IPv6 in my lab. I have tried several configuration scenarios with the typical "iface eth0 inet6 dhcp" in both "/etc/network/interfaces" as well as "/etc/network/interfaces.d/50-cloud-init.cfg" both within the container. I am running a standard bridge "br0" on the LXD host. I have tried configuring the LXD bridge to use "br0" as well as disabling it for a completely manual configuration. No success. I dont know if it is a timing issue or what. A key piece of information is once the container boots, I can run a "dhclient -6" command and it instantly obtains an IPv6 DHCP address... it just will not do it at boot time.

---

