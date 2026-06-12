---
title: "limit on VNET interfaces with KVM"
date: 2012-01-31
forum: Server Platforms
---

### Post by ragnarok189 on 2012-01-31
Hi all,

I administer a Dell Poweredge KVM hypervisor running 12 virtual machines. Previously all worked fine, last weekend we ran a maintenance window and rebooted the hypervisor. Now I am having an issue where a couple of guests cannot reach a network. I have two physical interfaces connected. One I reserve for host access, the other is bridged to br0. Both are statically assigned to the same subnet, only one has a gateway. Each guest is networked bridge mode to br0 and each guest has a unique mac address. I can see when each guest starts it grabs vnet0, vnet1, etc, sequentially. Vnet0 through vnet9 keep consistently working. The machine that grabs vnet10 is the first to break, and all others to follow. No amount of restarting networking, guest or host, will enable that connection. No iptables. Dhcp or static on the guest, same result. Also, I change which order guests are started, and the issue moves with the vnet, not the guest.

It appears to be related to the number of vnet interfaces connected to the bridge. All the log files pertaining to the vnets show no warnings or errors. Does anybody know about an actual limit to the number of vnets on a bridge, or macs listening to an eth?

We are currently trying to transition our virtual environment from a Xen/Citrix hybrid hosting environment to a homogenous system of KVM servers, but this is causing headaches and losing political support from upper management.

Server is Ubuntu 10.04.3. Evergthing else is up to date on the server. Most guests are lucid, one hardy, one centos, and two 2008r2's.

Ragnarok189

---

### Post by ragnarok189 on 2012-03-06
Ran into this issue again this morning.

Does anybody have any advice??

---

