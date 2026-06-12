---
title: "Lost Network when changing MTU size"
date: 2008-05-01
forum: Server Platforms
---

### Post by Termi11 on 2008-05-01
Hello,

i installed Ubuntu 8.04 on my Via C7 Epia SN1800G on an CF-Card.
Everything went fine. After installation i setup samba, changed the mtu size to 7000 and transferred some files to my disks (Raid 1 2*WD 500MB).
Speed about 40MB/sec)

Then i compiled a new Kernel (2.6.25).

Now, when i set the mtu size to 7000, and make a dmesg in an ssh terminal(or transfer files via ftp or samba), the network does not work anymore. Also a ping from the server to any other host in the network does not work anymore. When changing back the mtu size to 1500 without restarting, the network is ok (but a lot slower).

Also when booting the Original Ubuntu Kernel, i have now this problem.

> dirk@nas:~$ dmesg | grep eth
[   15.346556] eth0: VIA Networking Velocity Family Gigabit Ethernet Adapter
[   15.346556] eth0: Ethernet Address: 00:40:63:F4:4E:67
[   15.367932] eth1: VIA Rhine II at 0xfcfff400, 00:40:63:f4:4e:66, IRQ 23.
[   15.368701] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   15.394117] Driver 'sd' needs updating - please use bus_type methods
[   16.098579] Driver 'sr' needs updating - please use bus_type methods
[   23.816700] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.216470] eth0: Link auto-negotiation speed 1000M bps full duplex
[   25.217384] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   35.752189] eth0: no IPv6 routers present
[   69.040447] eth0: Link auto-negotiation speed 1000M bps full duplex
[  160.864140] eth0: Link auto-negotiation speed 1000M bps full duplex


NO error message in the log, when the network is lost.

What could be the problem? 

Thanks for help!!

---

