---
title: "Unable to access apache"
date: 2017-06-16
forum: Virtualisation
---

### Post by jeevansai2 on 2017-06-16
I am running apache server on guest system in virtualbox, but i was not able to access it from host i tried port forwarding method but of no use can someone explain how to access apache in guest from host.

---

### Post by SeijiSensei on 2017-06-16
Use bridged networking.  Then the guest will receive an IP on the same network as the host.  Otherwise you have to tunnel the connection through using iptables which is a lot more effort.  In VirtualBox go to Settings > Network for the virtual machine and select "bridged" from the drop-down box.

---

### Post by efflandt on 2017-06-16
If you "only" wanted to access it from the host there is a way to have an internal network to the host. But if you want your virtual system accessible to the host, LAN, and beyond, you need to used "bridged" for the network in virtualbox settings instead of NAT. If you have DHCP on your LAN your guest would automatically get a LAN IP, but you may want to configure static LAN IP if you intend to have it accessible from the Internet for ease of port forwarding on your router. Note that the guest bridged network connection and IP will NOT show up in ifconfig output on the host. But the host should be able to ping or connect to guest's IP.

---

