---
title: "KVM server configuration issue with multiple NICs (network interfaces)"
date: 2013-05-07
forum: Virtualisation
---

### Post by latimerio on 2013-05-07
These days most servers have more than 1 network interface and thus it is common to route traffic from kvm guests through specific NICs.
My server has 4 NICs and I plan to use eth0 as the default 100Mbit managment interface for the server and eth2 as gigabit ethernet for guests.
Eth1 will be the iSCSI interface to the storage and eth3 is spare for future guests.
Eth0 and eth2 connect to the same network (192.168.168.0)
I found many descriptions of network configurations with only 1 NIC but nothing for a multi NIC setup.

My understanding is that I need to bridge eth2 with the virtual network adapter of the KVM guests but I do not know how to properly setup the interfaces for this.
I guess it is best to have a static IP for eth0 although I would rather run dhcp using a reservation on the dhcp server.
The guest should use dhcp to get their IPs through the bridged eth2.

How do I need to configure the bridge and eth2 so that the server uses eth0 only and the guests use eth2?

---

