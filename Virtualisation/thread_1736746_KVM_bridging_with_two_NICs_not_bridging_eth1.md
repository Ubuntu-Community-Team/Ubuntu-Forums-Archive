---
title: "KVM bridging with two NICs not bridging eth1"
date: 2011-04-22
forum: Virtualisation
---

### Post by th0th696 on 2011-04-22
So I've had a bridged network working just fine with one NIC for awhile, where the host machine uses eth0 and the virtual machines receive their own static IP addresses.  Now I have a second NIC in the machine and would like to connect it to my LAN for some virtual internal servers.  My /etc/network/interfaces looks like so:

[http://paste.pocoo.org/show/376433/](http://paste.pocoo.org/show/376433/)

which I made from following the directions on this page:

[https://help.ubuntu.com/community/KVM/Networking#bridgednetworking](https://help.ubuntu.com/community/KVM/Networking#bridgednetworking)

But still virt-manager, shows only vnet's for br0 and none for br1.  Is there something I need to do to tell virt-manager about br1?

---

