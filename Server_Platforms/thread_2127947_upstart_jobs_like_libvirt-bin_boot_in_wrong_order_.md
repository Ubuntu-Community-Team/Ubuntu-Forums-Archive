---
title: "upstart jobs like libvirt-bin boot in wrong order ..."
date: 2013-03-21
forum: Server Platforms
---

### Post by ufpirate on 2013-03-21
Hello, I don't know if this is the right place for this problem, but I try...


Config : ubuntu 12.04LTS server, AMD-Opteron Quad, 8GB. 90GB SSD as sda, 1TB as lvm1 and 500GB as lvm2, 4 nics
Installation Order:
1. Ubuntu
2. kvm-qemu
3. libvirt, virtinst
4. ovs (open virtual switch)
5. recompiled ovs to 1.99, and setup 2nic bonds on 2 bridges ovsbr0,1. works.
6. recompiled libvirt to 1.0.3 <- works

now I rebooted the machine and found out that the services start in some wrong order.
1. Networking starts <-OK
2. Libvirt tries to start <- fails since it taps to the virtual switch which did not fully start yet -> retries approx. 10 times and fails
3. ovs starts and works.
4. qemu starts and works.

At this time if you look on the ovs there are no taps used by the virtual machines.

 [COLOR=#a9a9a9]root@srv1:~# ovs-vsctl show
    Bridge "ovsbr0"
        Port "ovsbr0"
            Interface "ovsbr0"
                type: internal
        Port "bond0"
            Interface "eth0"
            Interface "eth1"
    Bridge "ovsbr1"
        Port "ovsbr1"
            Interface "ovsbr1"
                type: internal
        Port "bond1"
            Interface "eth3"
            Interface "eth2"
    ovs_version: "1.10.0"[/COLOR]

I log in via ssh or go to the machine and manually start libvirt via: service libvirt-bin start and both vm start no error no problem.

 [COLOR=#a9a9a9]Bridge "ovsbr0"
        Port "ovsbr0"
            Interface "ovsbr0"
                type: internal
        Port "bond0"
            Interface "eth0"
            Interface "eth1"
    Bridge "ovsbr1"
        Port "tap4"
            Interface "tap4"   [/COLOR][COLOR=#000000]<--- ok virtual2 machine tapped in [/COLOR][COLOR=#a9a9a9]
        Port "ovsbr1"
            Interface "ovsbr1"
                type: internal
        Port "tap1"[/COLOR][COLOR=#000000]
            [/COLOR][COLOR=#808080]Interface "tap1"[/COLOR][COLOR=#000000] <--- ok virtual1 machine tapped in [/COLOR][COLOR=#a9a9a9]
        Port "bond1" 
            Interface "eth3"
            Interface "eth2"[/COLOR]



I tried already a lot of startup modifications but could not make it work. 

Now I look at dmesg and believe to see what I tried to describe:
...
[COLOR=#696969][   12.911519] openvswitch: Open vSwitch switching datapath 1.10.0, 
[   12.961889] init: libvirt-bin main process (1420) terminated with status 6
[   12.961918] init: libvirt-bin main process ended, respawning
[   12.980319] init: libvirt-bin main process (1457) terminated with status 6
[   12.980353] init: libvirt-bin main process ended, respawning
[   12.998478] init: libvirt-bin main process (1473) terminated with status 6
[   12.998506] init: libvirt-bin main process ended, respawning
[   13.019997] init: libvirt-bin main process (1490) terminated with status 6
[   13.020025] init: libvirt-bin main process ended, respawning
[   13.039021] init: libvirt-bin main process (1506) terminated with status 6
[   13.039057] init: libvirt-bin main process ended, respawning
[   13.057364] init: libvirt-bin main process (1535) terminated with status 6
[   13.057399] init: libvirt-bin main process ended, respawning
[   13.074709] init: libvirt-bin main process (1551) terminated with status 6
[   13.074743] init: libvirt-bin main process ended, respawning
[   13.092467] init: libvirt-bin main process (1567) terminated with status 6
[   13.092502] init: libvirt-bin main process ended, respawning
[   13.111538] init: libvirt-bin main process (1587) terminated with status 6
[   13.111567] init: libvirt-bin main process ended, respawning
[   13.130578] init: libvirt-bin main process (1613) terminated with status 6
[   13.130605] init: libvirt-bin main process ended, respawning
[   13.131653] device ovs-system entered promiscuous mode
[   13.135076] device ovsbr0 entered promiscuous mode
[   13.151577] device eth0 entered promiscuous mode
[   13.151768] device eth1 entered promiscuous mode
[   13.155033] device bond0 entered promiscuous mode
[   13.157097] init: libvirt-bin main process (1667) terminated with status 6
[   13.157135] init: libvirt-bin respawning too fast, stopped
[   13.224100] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.226401] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   13.248288] e1000: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[   13.249102] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   13.374120] device ovsbr1 entered promiscuous mode
[   13.387922] device eth3 entered promiscuous mode
[   13.388543] device eth2 entered promiscuous mode
[   13.391113] device bond1 entered promiscuous mode
[   13.400233] r8169 0000:05:06.0: eth2: link down
[   13.400268] r8169 0000:05:06.0: eth2: link down
[   13.401210] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[   13.541498] r8169 0000:07:00.0: eth3: link down
[   13.541537] r8169 0000:07:00.0: eth3: link down
[   13.542225] IPv6: ADDRCONF(NETDEV_UP): eth3: link is not ready
[   15.938765] r8169 0000:07:00.0: eth3: link up
[   15.939404] IPv6: ADDRCONF(NETDEV_CHANGE): eth3: link becomes ready
[   16.236743] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   16.237547] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   16.580684] r8169 0000:05:06.0: eth2: link up
[   16.581312] IPv6: ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[   29.010987] Bridge firewalling registered
[   29.030915] device virbr0-nic entered promiscuous mode
[   29.102636] ip_tables: (C) 2000-2006 Netfilter Core Team
[   29.172368] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   29.195011] virbr0: topology change detected, propagating
[   29.195018] virbr0: port 1(virbr0-nic) entered forwarding state
[   29.195039] virbr0: port 1(virbr0-nic) entered forwarding state
[   29.204545] virbr0: port 1(virbr0-nic) entered disabled state
[   29.959122] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   30.823071] device tap4 entered promiscuous mode
[   31.198194] device tap1 entered promiscuous mode
[   38.722021] kvm: 2624: cpu0 unhandled rdmsr: 0xc0010001
[   39.075797] kvm: 2643: cpu0 unhandled rdmsr: 0xc0010001
[ 1148.661715] EXT4-fs (md126): Cannot change data mode on remount
[ 1157.513447] EXT4-fs (md126): Cannot change data mode on remount
[ 1191.700724] device tap4 left promiscuous mode
[ 1194.298823] device tap1 left promiscuous mode
[ 1263.492011] EXT4-fs (md126): Ignoring removed nobh option
[ 1263.504644] EXT4-fs (md126): barriers disabled
[ 1263.547396] EXT4-fs (md126): mounted filesystem with writeback data mode. Opts: data=writeback,barrier=0,nobh,errors=remount-ro
[52896.962555] CE: hpet increased min_delta_ns to 20113 nsec
[84416.311393] device tap4 entered promiscuous mode
[84416.610739] device tap1 entered promiscuous mode
[84424.078541] kvm: 6087: cpu0 unhandled rdmsr: 0xc0010001
[84424.416958] kvm: 6105: cpu0 unhandled rdmsr: 0xc0010001[/COLOR]
...

all the best to you giving some comments to this to get me to a fully/not semi working system ;-)

seth traend

---

