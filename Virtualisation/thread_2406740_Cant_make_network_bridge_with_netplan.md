---
title: "Cant make network bridge with netplan"
date: 2018-11-25
forum: Virtualisation
---

### Post by richard-hocking on 2018-11-25
This is my first effort trying to get a network bridge up using netplan.

netplan config file
```
# This file is generated from information provided by the datasource.  Changes to it will not persist across an instance.# To disable cloud-init's network configuration capabilities, write a file# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    renderer: networkd
    ethernets:
        enp0s25:
            addresses: [192.168.1.2/24]
            gateway4: 192.168.1.1
            nameservers:
              addresses: [61.9.194.49,67.9.195.193]
            dhcp4: no
#    bridges:
#        br0:
#            dhcp4: no
#            addresses: [192.168.1.90/24]
#            gateway4: 192.168.1.1
#            interfaces: [enp0s25]
```

The /var/syslog after I entered
 
```
$ sudo netplan apply
```

```
Nov 25 06:35:45 milliways systemd[1]: Stopped Wait for Network to be Configured.Nov 25 06:35:45 milliways systemd[1]: Stopping Network Service...
Nov 25 06:35:45 milliways systemd-timesyncd[878]: Network configuration changed, trying to establish connection.
Nov 25 06:35:45 milliways systemd[1]: Starting Network Service...
Nov 25 06:35:45 milliways snapd[1195]: udevmon.go:184: udev monitor observed remove event for unknown device "/sys/kernel/slab/:A-0000072/cgroup/eventpoll_pwq(648:systemd-networkd.service)"
Nov 25 06:35:45 milliways snapd[1195]: udevmon.go:184: udev monitor observed remove event for unknown device "/sys/kernel/slab/:A-0000128/cgroup/eventpoll_epi(648:systemd-networkd.service)"
Nov 25 06:35:45 milliways snapd[1195]: udevmon.go:184: udev monitor observed remove event for unknown device "/sys/kernel/slab/:A-0000256/cgroup/filp(648:systemd-networkd.service)"
Nov 25 06:35:45 milliways snapd[1195]: udevmon.go:184: udev monitor observed remove event for unknown device "/sys/kernel/slab/:A-0000208/cgroup/vm_area_struct(648:systemd-networkd.service)"
Nov 25 06:35:45 milliways snapd[1195]: udevmon.go:184: udev monitor observed remove event for unknown device "/sys/kernel/slab/:0000256/cgroup/kmalloc-256(648:systemd-networkd.service)"
Nov 25 06:35:45 milliways snapd[1195]: udevmon.go:184: udev monitor observed remove event for unknown device "/sys/kernel/slab/:0000512/cgroup/kmalloc-512(648:systemd-networkd.service)"
Nov 25 06:35:45 milliways snapd[1195]: udevmon.go:184: udev monitor observed remove event for unknown device "/sys/kernel/slab/:0001024/cgroup/kmalloc-1024(648:systemd-networkd.service)"
Nov 25 06:35:45 milliways snapd[1195]: udevmon.go:184: udev monitor observed remove event for unknown device "/sys/kernel/slab/:A-0000064/cgroup/pid(648:systemd-networkd.service)"
Nov 25 06:35:45 milliways snapd[1195]: udevmon.go:184: udev monitor observed remove event for unknown device "/sys/kernel/slab/sock_inode_cache/cgroup/sock_inode_cache(648:systemd-networkd.service)"
Nov 25 06:35:45 milliways snapd[1195]: udevmon.go:184: udev monitor observed remove event for unknown device "/sys/kernel/slab/:A-0002112/cgroup/mm_struct(648:systemd-networkd.service)"
Nov 25 06:35:45 milliways snapd[1195]: udevmon.go:184: udev monitor observed remove event for unknown device "/sys/kernel/slab/anon_vma/cgroup/anon_vma(648:systemd-networkd.service)"
Nov 25 06:35:45 milliways snapd[1195]: udevmon.go:184: udev monitor observed remove event for unknown device "/sys/kernel/slab/:A-0000192/cgroup/cred_jar(648:systemd-networkd.service)"
Nov 25 06:35:45 milliways systemd-networkd[2746]: br0: netdev ready
Nov 25 06:35:45 milliways systemd-networkd[2746]: veth66777d2: Gained IPv6LL
Nov 25 06:35:45 milliways systemd-udevd[2767]: link_config: autonegotiation is unset or enabled, the speed and duplex are not writable.
Nov 25 06:35:45 milliways systemd-networkd[2746]: docker0: Gained IPv6LL
Nov 25 06:35:45 milliways systemd-networkd[2746]: enp0s25: Gained IPv6LL
Nov 25 06:35:45 milliways systemd-networkd[2746]: Enumeration completed
Nov 25 06:35:45 milliways systemd[1]: Started Network Service.
Nov 25 06:35:45 milliways kernel: [  753.903353] e1000e: enp0s25 NIC Link is Down
Nov 25 06:35:45 milliways kernel: [  753.903925] br0: port 1(enp0s25) entered blocking state
Nov 25 06:35:45 milliways kernel: [  753.903927] br0: port 1(enp0s25) entered disabled state
Nov 25 06:35:45 milliways kernel: [  753.904003] device enp0s25 entered promiscuous mode
Nov 25 06:35:45 milliways kernel: [  753.904883] IPv6: ADDRCONF(NETDEV_UP): br0: link is not ready
Nov 25 06:35:45 milliways networkd-dispatcher[1119]: WARNING:Unknown index 6 seen, reloading interface list
Nov 25 06:35:45 milliways systemd-networkd[2746]: veth66777d2: Link is not managed by us
Nov 25 06:35:45 milliways systemd-networkd[2746]: lo: Link is not managed by us
Nov 25 06:35:45 milliways systemd-networkd[2746]: docker0: Link is not managed by us
Nov 25 06:35:45 milliways systemd-networkd[2746]: br0: IPv6 successfully enabled
Nov 25 06:35:45 milliways systemd-networkd[2746]: enp0s25: Lost carrier
Nov 25 06:35:45 milliways systemd-networkd[2746]: enp0s25: IPv6 successfully disabled
Nov 25 06:35:45 milliways kernel: [  754.108495] br0: port 1(enp0s25) entered blocking state
Nov 25 06:35:45 milliways kernel: [  754.108499] br0: port 1(enp0s25) entered forwarding state
Nov 25 06:35:45 milliways kernel: [  754.108543] IPv6: ADDRCONF(NETDEV_CHANGE): br0: link becomes ready
Nov 25 06:35:45 milliways systemd-networkd[2746]: enp0s25: Gained carrier
Nov 25 06:35:45 milliways systemd-networkd[2746]: br0: Gained carrier
Nov 25 06:35:45 milliways systemd-networkd[2746]: enp0s25: Configured
Nov 25 06:35:46 milliways systemd-networkd[2746]: enp0s25: Lost carrier
Nov 25 06:35:46 milliways kernel: [  754.808495] br0: port 1(enp0s25) entered disabled state
Nov 25 06:35:46 milliways systemd-networkd[2746]: br0: Gained IPv6LL
Nov 25 06:35:46 milliways systemd-networkd[2746]: br0: Configured
Nov 25 06:35:47 milliways systemd-networkd[2746]: br0: Lost carrier
Nov 25 06:35:48 milliways kernel: [  757.490497] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Nov 25 06:35:48 milliways kernel: [  757.490556] br0: port 1(enp0s25) entered blocking state
Nov 25 06:35:48 milliways kernel: [  757.490559] br0: port 1(enp0s25) entered forwarding state
Nov 25 06:35:48 milliways systemd-networkd[2746]: enp0s25: Gained carrier
Nov 25 06:35:48 milliways systemd-networkd[2746]: br0: Gained carrier
Nov 25 06:35:48 milliways systemd-networkd[2746]: enp0s25: Configured
Nov 25 06:35:48 milliways systemd-networkd[2746]: br0: Configured
Nov 25 06:35:55 milliways systemd-timesyncd[878]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
Nov 25 06:36:05 milliways systemd-timesyncd[878]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
Nov 25 06:36:14 milliways systemd[1]: Stopping Network Service...
Nov 25 06:36:14 milliways systemd[1]: Starting Network Service...
Nov 25 06:36:14 milliways systemd-networkd[2791]: br0: netdev ready
Nov 25 06:36:14 milliways systemd-networkd[2791]: br0: Gained IPv6LL
Nov 25 06:36:14 milliways systemd-networkd[2791]: veth66777d2: Gained IPv6LL
Nov 25 06:36:14 milliways systemd-networkd[2791]: docker0: Gained IPv6LL
Nov 25 06:36:14 milliways systemd-networkd[2791]: Enumeration completed
Nov 25 06:36:14 milliways systemd[1]: Started Network Service.
Nov 25 06:36:14 milliways systemd-networkd[2791]: br0: netdev exists, using existing without changing its parameters
Nov 25 06:36:14 milliways systemd-networkd[2791]: docker0: Link is not managed by us
Nov 25 06:36:14 milliways systemd-networkd[2791]: enp0s25: Link is not managed by us
Nov 25 06:36:14 milliways systemd-networkd[2791]: lo: Link is not managed by us
Nov 25 06:36:14 milliways systemd-networkd[2791]: veth66777d2: Link is not managed by us
Nov 25 06:36:14 milliways kernel: [  783.656519] e1000e: enp0s25 NIC Link is Down
Nov 25 06:36:14 milliways kernel: [  783.656690] br0: port 1(enp0s25) entered disabled state
Nov 25 06:36:15 milliways systemd-networkd[2791]: enp0s25: Lost carrier
Nov 25 06:36:15 milliways systemd-networkd[2791]: br0: Lost carrier
Nov 25 06:36:15 milliways systemd-networkd[2791]: enp0s25: IPv6 successfully disabled
Nov 25 06:36:15 milliways systemd-networkd[2791]: br0: Configured
Nov 25 06:36:15 milliways systemd-timesyncd[878]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
Nov 25 06:36:18 milliways kernel: [  787.243702] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Nov 25 06:36:18 milliways kernel: [  787.243759] br0: port 1(enp0s25) entered blocking state
Nov 25 06:36:18 milliways kernel: [  787.243763] br0: port 1(enp0s25) entered forwarding state
Nov 25 06:36:18 milliways systemd-networkd[2791]: enp0s25: Gained carrier
Nov 25 06:36:18 milliways systemd-networkd[2791]: br0: Gained carrier
Nov 25 06:36:18 milliways systemd-networkd[2791]: enp0s25: Configured
Nov 25 06:36:18 milliways systemd-networkd[2791]: br0: Configured
Nov 25 06:37:00 milliways systemd[1]: Starting Message of the Day...
Nov 25 06:37:00 milliways systemd-resolved[933]: Using degraded feature set (UDP) for DNS server 67.9.195.193.
Nov 25 06:37:05 milliways systemd-resolved[933]: Using degraded feature set (UDP) for DNS server 61.9.194.49.
Nov 25 06:37:11 milliways systemd[1]: Started Message of the Day.
```

Thanks for any help

---

### Post by Tadaen_Sylvermane on 2018-11-26
I don't know about using a different ip for both the interface and the bridge. However I do know that yaml files use spaces and not tabs, not just white space. If you are using tabs then it simply won't work. Single space indentation is required.

---

