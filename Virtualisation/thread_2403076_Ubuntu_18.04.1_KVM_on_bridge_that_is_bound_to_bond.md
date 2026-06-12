---
title: "Ubuntu 18.04.1 KVM on bridge that is bound to bonded interfaces. Bonding doesn't work"
date: 2018-10-07
forum: Virtualisation
---

### Post by chrishapunkt2 on 2018-10-07
Hello helpful people :)


I'm trying to speed up my NAS server's network speed. So I decided to bond two 1GBit NICs in the server.


The NAS itself is running as a KVM on that server. I'm using virt-manager to manage the VM.


Network settings in virt-manager are as follows:


"Network source: Bridge br1: Host device bond0"
"Device model rtl8139"
"Mac address: 52:54:00:10:bf:ac"


Here is the host's /etc/network/interfaces/file


```

auto bond0
iface bond0 inet manual
bond-lacp-rate 1
post-up ifenslave bond0 enp66s0 enp4s0
pre-down ifenslave -d bond0 enp66s0 enp4s0
bond-slaves none
bond mode 0
bond-lacp-rate fast
bond-miimon 100
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1


auto enp4s0
iface enp4s0 inet manual
bond-master bond0


auto enp66s0
iface enp66s0 inet manual
bond-master bond0


auto br1
iface br1 inet dhcp
  bridge-ports bond0
  bridge-fd 9
  bridge-hello 2
  bridge-maxage 12
  bridge-stp on

```


Now the problem is that the KVM does not get a network connection via the bridge like it did before when I wasn't using the bonded network interfaces.


The output of ip addr on the host before I start the VM


```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 00:23:7d:21:92:be brd ff:ff:ff:ff:ff:ff
3: enp66s0: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP group default qlen 1000
    link/ether 00:23:7d:21:92:bc brd ff:ff:ff:ff:ff:ff
4: bond0: <BROADCAST,MULTICAST,MASTER,UP,LOWER_UP> mtu 1500 qdisc noqueue master br1 state UP group default qlen 1000
    link/ether 00:23:7d:21:92:bc brd ff:ff:ff:ff:ff:ff
    inet6 fe80::223:7dff:fe21:92bc/64 scope link 
       valid_lft forever preferred_lft forever
5: br1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 00:23:7d:21:92:bc brd ff:ff:ff:ff:ff:ff
    inet 192.168.4.132/24 brd 192.168.4.255 scope global br1
       valid_lft forever preferred_lft forever
    inet6 fe80::223:7dff:fe21:92bc/64 scope link 
       valid_lft forever preferred_lft forever
6: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:c7:4d:0e brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
7: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr0 state DOWN group default qlen 1000
    link/ether 52:54:00:c7:4d:0e brd ff:ff:ff:ff:ff:ff

```


IP addr on the host after I started the VM:


```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 00:23:7d:21:92:be brd ff:ff:ff:ff:ff:ff
3: enp66s0: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP group default qlen 1000
    link/ether 00:23:7d:21:92:bc brd ff:ff:ff:ff:ff:ff
4: bond0: <BROADCAST,MULTICAST,MASTER,UP,LOWER_UP> mtu 1500 qdisc noqueue master br1 state UP group default qlen 1000
    link/ether 00:23:7d:21:92:bc brd ff:ff:ff:ff:ff:ff
    inet6 fe80::223:7dff:fe21:92bc/64 scope link 
       valid_lft forever preferred_lft forever
5: br1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 00:23:7d:21:92:bc brd ff:ff:ff:ff:ff:ff
    inet 192.168.4.132/24 brd 192.168.4.255 scope global br1
       valid_lft forever preferred_lft forever
    inet6 fe80::223:7dff:fe21:92bc/64 scope link 
       valid_lft forever preferred_lft forever
6: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:c7:4d:0e brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
7: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr0 state DOWN group default qlen 1000
    link/ether 52:54:00:c7:4d:0e brd ff:ff:ff:ff:ff:ff
8: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br1 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:10:bf:ac brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fe10:bfac/64 scope link 
       valid_lft forever preferred_lft forever

```


The output of ip addr in the VM before I unplug the cable:


```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: ens3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 52:54:00:10:bf:ac brd ff:ff:ff:ff:ff:ff
    inet 192.168.4.195/24 brd 192.168.4.255 scope global ens3
       valid_lft forever preferred_lft forever

```


When I unplug the cable of enp66s0, it says 'copper link is down' and all connections break. (SSH to the host, a ping running on the host to google or any network device starts to fail, ping inside the VM starts to fail).
If I unplug enp4s0, nothing happens (it doensn't say that the copper link is down).




When I shut down the VM, ip addr on the host looks like this


```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 00:23:7d:21:92:be brd ff:ff:ff:ff:ff:ff
3: enp66s0: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP group default qlen 1000
    link/ether 00:23:7d:21:92:bc brd ff:ff:ff:ff:ff:ff
4: bond0: <BROADCAST,MULTICAST,MASTER,UP,LOWER_UP> mtu 1500 qdisc noqueue master br1 state UP group default qlen 1000
    link/ether 00:23:7d:21:92:bc brd ff:ff:ff:ff:ff:ff
    inet6 fe80::223:7dff:fe21:92bc/64 scope link 
       valid_lft forever preferred_lft forever
5: br1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 00:23:7d:21:92:bc brd ff:ff:ff:ff:ff:ff
    inet 192.168.4.132/24 brd 192.168.4.255 scope global br1
       valid_lft forever preferred_lft forever
    inet6 fe80::223:7dff:fe21:92bc/64 scope link 
       valid_lft forever preferred_lft forever
6: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:c7:4d:0e brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
7: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr0 state DOWN group default qlen 1000
    link/ether 52:54:00:c7:4d:0e brd ff:ff:ff:ff:ff:ff

```


But the behaviour when unplugging enp66s0 is still that the ping on the host breaks and disconnect of enp4s0 is not recognized.12


So the bonding does not work anymore when the VM was running once.


What could be wrong?

---

### Post by KillerKelvUK on 2018-10-07
Maybe a useless post to you but I can't really help with bonding as I've never had the need but this sounds like your bonding is the issue as it doesn't know to fail back to a single unbonded connection when one physical interface is disconnected i.e. how does a single interface get an Ip given your hosts config.

Also maybe a little more useful...

> 
"Network source: Bridge br1: Host device bond0"
"Device model rtl8139"
"Mac address: 52:54:00:10:bf:ac"


Switch to using virtio instead of rtl8139, guest network throughput to host should then increase to 10Gb instead of the 1Gb I presume you are getting now per link.

---

### Post by kevin160 on 2018-10-15
Are you sure that your bonded interfaces are correctly configured on the switch they are connected to?  Some "smart" switches (for example, the little D-Link DGS-1100-08 I use in my living room) don't have LACP at all.   

It looks like you are using the virtualized "rtl" ethernet in your vm settings instead of the native virtio driver.  I don't know if this is the cause of your problem, but you definitely want to run with virtio adapters if your guest supports it.

If you can't get this working with linux bridging, you might try using Open vSwitch instead (apt install openvswitch-switch).  It's kind of overkill for a single server, but I've definitely had your use-case working.

---

