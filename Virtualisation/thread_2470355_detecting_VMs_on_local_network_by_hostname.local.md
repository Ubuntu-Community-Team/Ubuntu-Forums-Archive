---
title: "detecting VMs on local network by hostname.local?"
date: 2021-12-27
forum: Virtualisation
---

### Post by jfaberna on 2021-12-27
My homelab is a mixture of PC, raspberry pi's, and servers all on the same subnet. I can ssh into any of them using their /etc/hostname with dot 'local' as in ```
ssh jim@my-server.local
``` However, I can't do that to any of my VM's created with virt-manager. My VM are all connected to a local bridge I created, 'br0' and my eno1 is slaved to that bridge. If I know the IP address any PC can ssh into that VM, but using mDNS makes it easier for all my local servers. Just not working for VMs.

It is interesting that my AP/Router that provides the DHCP services to the whole network including VMs knows the VM hostnames and they are listed on the DHCP page on the router admin site.

Any idea on how to solve this?

---

### Post by jfaberna on 2021-12-27
I found a workaround. All the VM's were Ubuntu 20.04 server with just openssh as an additional package. Once I installed on the VMs the following:
```
sudo apt install avahi-daemon avahi-autoipd 

```I could then ssh into the VM using it's hostname.local from any PC on the local network.

---

