---
title: "modprobe gets stuck on a e1000e driver mutex wile trying to load it"
date: 2011-03-06
forum: Server Platforms
---

### Post by eddev on 2011-03-06
Hello,
I have an Intel® Server Board S5500BC which started to cause problems
during boot, mainly with the e1000e driver, raising the server without
any NIC/s. A reboot ususally recovers the NIC/s.
The following trace is seen from the unit boot, showing an
inconsistent problem while trying to load the e1000e driver.
Looking at the sources, it looks like it is stuck in a critical
section. But I frankly do not understand how it is possible, as there
is no real reason for it to hang on the mutex lock.
At the moment, except memory curroption/leak I cannot think of
anything else... I see it on several machines, so I assume it is not a
specific HW problem.
I will apriciate if someone could point me into some direction.
Note, the pasted message below repeats in a loop, always hangling on
the same lock. In addition, these units also hang from time to time on
initramfs shell, with an avarage of 3 times less frequent than the NIC
issue.
I'm using the following Kernel version:
```
Linux version 2.6.32-29-generic-pae (buildd@roseapple) (gcc version
4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #58-Ubuntu SMP Fri Feb 11 19:15:25 UTC
2011 (Ubuntu 2.6.32-29.58-generic-pae 2.6.32.28+drm33.13)
```
Thanks,
Edy.
 
This is the relevant trace from the dmesg output:
```

[    5.732070] lp: driver loaded but no devices found
[    6.002709] Console: switching to colour frame buffer device 80x30
[    6.023688] type=1505 audit(1299198224.576:5):
operation="profile_load" pid=820 name="/usr/sbin/tcpdump"
[    6.023858] type=1505 audit(1299198224.576:6):
operation="profile_replace" pid=819 name="/sbin/dhclient3"
[    6.024301] type=1505 audit(1299198224.576:7):
operation="profile_replace" pid=819
name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    6.024550] type=1505 audit(1299198224.576:8):
operation="profile_replace" pid=819
name="/usr/lib/connman/scripts/dhclient-script"
[    6.134782] ip_tables: (C) 2000-2006 Netfilter Core Team
[    6.177099] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    6.177269] CONFIG_NF_CT_ACCT is deprecated and will be removed
soon. Please use
[    6.177271] nf_conntrack.acct=1 kernel parameter, acct=1
nf_conntrack module option or
[    6.177273] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[  240.190031] INFO: task modprobe:178 blocked for more than 120 seconds.
[  240.190534] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs"
disables this message.
[  240.191160] modprobe      D 00183416     0   178      1 0x00000000
[  240.191169]  f6e8fd44 00000086 f829b248 00183416 00000000 c088f4c0
f6f85be4 c088f4c0
[  240.191186]  6c1f8881 00000000 c088f4c0 c088f4c0 f6f85be4 c088f4c0
c088f4c0 f6e3ea00
[  240.191202]  6a3827bd 00000000 f6f85940 f829b238 f829b23c ffffffff
f6e8fd70 c05b3bb6
[  240.191216] Call Trace:
[  240.191231]  [<c05b3bb6>] __mutex_lock_slowpath+0xd6/0x140
[  240.191239]  [<c05b3ac5>] mutex_lock+0x25/0x40
[  240.191255]  [<f8285be1>] e1000_acquire_swflag_ich8lan+0x21/0xa0 [e1000e]
[  240.191270]  [<f8286aea>] e1000_reset_hw_ich8lan+0x7a/0x250 [e1000e]
[  240.191287]  [<f82940bd>] e1000e_reset+0xfd/0x330 [e1000e]
[  240.191302]  [<f82984e8>] e1000_probe+0x7b7/0xa09 [e1000e]
[  240.191309]  [<c0227745>] ? iput+0x25/0x60
[  240.191316]  [<c026af3b>] ? sysfs_addrm_finish+0x3b/0xf0
[  240.191325]  [<c0370043>] local_pci_probe+0x13/0x20
[  240.191331]  [<c0370e48>] pci_device_probe+0x68/0x90
[  240.191339]  [<c03fceed>] really_probe+0x4d/0x140
[  240.191347]  [<c040380e>] ? pm_runtime_barrier+0x4e/0xc0
[  240.191354]  [<c03fd01c>] driver_probe_device+0x3c/0x60
[  240.191361]  [<c03fd0c1>] __driver_attach+0x81/0x90
[  240.191368]  [<c03fc503>] bus_for_each_dev+0x53/0x80
[  240.191375]  [<c03fcdbe>] driver_attach+0x1e/0x20
[  240.191382]  [<c03fd040>] ? __driver_attach+0x0/0x90
[  240.191389]  [<c03fc785>] bus_add_driver+0xd5/0x280
[  240.191396]  [<c0370d80>] ? pci_device_remove+0x0/0x40
[  240.191403]  [<c03fd3ba>] driver_register+0x6a/0x130
[  240.191410]  [<c0371085>] __pci_register_driver+0x45/0xb0
[  240.191423]  [<f82a304b>] e1000_init_module+0x4b/0x67 [e1000e]
[  240.191430]  [<c0103041>] do_one_initcall+0x31/0x190
[  240.191443]  [<f82a3000>] ? e1000_init_module+0x0/0x67 [e1000e]
[  240.191452]  [<c018acb0>] sys_init_module+0xb0/0x210
[  240.191458]  [<c01097ac>] syscall_call+0x7/0xb
 
lshw network output:
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 00
       serial: 00:1b:21:57:0a:54
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list rom
ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd
autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=e1000e
driverversion=1.0.2-k2 duplex=full firmware=1.8-0 ip=127.0.1.1
latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:b1a80000-b1a9ffff
memory:b1a00000-b1a7ffff ioport:2000(size=32) memory:b1aa0000-b1aa3fff
memory:b1c00000-b1c3ffff(prefetchable)
  *-network
       description: Ethernet interface
       product: 82578DM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 00:15:17:c8:0a:3d
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp
10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=e1000e
driverversion=1.0.2-k2 duplex=full firmware=0.9-2 ip=127.0.0.1
latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:34 memory:b1b00000-b1b1ffff
memory:b1b24000-b1b24fff ioport:3020(size=32)
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 00
       serial: 00:15:17:c8:0a:3c
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd
autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e
driverversion=1.0.2-k2 duplex=full firmware=1.9-0 ip=172.17.6.2
latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:b1900000-b191ffff ioport:1000(size=32)
memory:b1920000-b1923fff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: eth1.24
       serial: 00:1b:21:57:0a:54
       size: 100MB/s
       capacity: 1GB/s
       capabilities: ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd
1000bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=802.1Q
VLAN Support driverversion=1.8 duplex=full firmware=N/A link=yes
multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: vlan24
       serial: 00:15:17:c8:0a:3d
       size: 100MB/s
       capacity: 1GB/s
       capabilities: ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd
1000bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=802.1Q
VLAN Support driverversion=1.8 duplex=full firmware=N/A
ip=172.24.4.182 link=yes multicast=yes port=twisted pair speed=100MB/s

```

---

