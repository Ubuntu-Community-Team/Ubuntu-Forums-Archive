---
title: "Need help with virtual network config"
date: 2013-10-10
forum: Virtualisation
---

### Post by ReichhartKG on 2013-10-10
As shown in the crappy diagram below, I have two KVM hosts and a router.  Each KVM host has several guests.  For clarity, I've only shown one guest on each host.

On each host, vmbr0 is bound to eth0.  On each guest, eth0 is bound to vmbr0 on the host.
On each host, eth1 and eth2 create bond0.  Bond0 is split into VLANs bond0.1, bond0.2, and bond0.3.  Bond0.1, bond0.2, and bond0.3 are bound to vmbr1, vmbr2, and vmbr3, respectively.  On each guest, eth1, eth2, and eth3 are bound to vmbr1, vmbr2, and vmbr3.

router eth0 = internet
router eth1 / host vmbr0 / guest eth0 = 10.69.0.0/24
router bond0.1 / host vmbr1 / guest eth1 = 10.69.1.0/24
router bond0.2 / host vmbr2 / guest eth2 = 10.69.2.0/24
router bond0.3 / host vmbr3 / guest eth3 = 10.69.3.0/24
router bond0 / host bond0 = 192.168.16.0/24

Router can ping all IPs on both hosts and all IPs on both guests
Host 1 can ping all IPs on host 2, all IPs on router, and all IPs on both guests
Host 2 can ping all IPs on host 1, all IPs on router, and all IPs on both guests
Guest 1 can ping all IPs on host 1
Guest 2 can ping all IPs on host 2

The problem is...
Host 1 can only ping the 10.69.0.0/24 IP on guest 2
Host 2 can only ping the 10.69.0.0/24 IP on guest 1
Guest 1 can only ping the 10.69.0.0/24 IP on router, host 2, and guest 2
Guest 2 can only ping the 10.69.0.0/24 IP on router, host 1, and guest 1

/var/log/messages is full of messages like this:
Oct 10 23:44:17 kvm2 kernel: martian source 10.69.1.24 from 10.69.1.66, on dev vmbr1
Oct 10 23:44:17 kvm2 kernel: ll header: ff:ff:ff:ff:ff:ff:00:23:7d:5d:7e:68:08:06
Oct 10 23:44:20 kvm2 kernel: bond0.1: received packet with own address as source address
Oct 10 23:44:20 kvm2 kernel: martian source 10.69.1.23 from 10.69.1.66, on dev vmbr1
Oct 10 23:44:20 kvm2 kernel: ll header: ff:ff:ff:ff:ff:ff:00:23:7d:5d:7e:68:08:06
Oct 10 23:45:12 kvm2 kernel: bond0.1: received packet with own address as source address
Oct 10 23:45:12 kvm2 kernel: bond0.1: received packet with own address as source address
Oct 10 23:45:14 kvm2 kernel: bond0.2: received packet with own address as source address
Oct 10 23:45:14 kvm2 kernel: bond0.2: received packet with own address as source address
Oct 10 23:45:15 kvm2 kernel: bond0.3: received packet with own address as source address
Oct 10 23:45:15 kvm2 kernel: bond0.3: received packet with own address as source address
Oct 10 23:45:16 kvm2 kernel: bond0: received packet with own address as source address
Oct 10 23:45:16 kvm2 kernel: bond0: received packet with own address as source address


I think it's an ARP issue that requires a little sysctl love to remedy and/or that the hosts aren't happy about the martians, but I haven't done much troubleshooting yet.

[IMG]http://reichhartconsulting.com/images/kvm_net_diagram.png[/IMG]

---

