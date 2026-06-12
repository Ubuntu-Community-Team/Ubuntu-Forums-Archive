---
title: "KVM network bridge with Open vSwitch issues"
date: 2014-07-31
forum: Server Platforms
---

### Post by kosmokramer314 on 2014-07-31
Not able to get an IP address assigned to a ubuntu VM.  I'm able to launch the VM that I created with virt-manager and login via the console, but there is no network connection.  I'm not really sure where the issue is.  

EDIT:  I followed this guide [http://www.rivy.org/2014/04/install-a-kvm-host-on-ubuntu-14-04-trusty-tahr/]("http://www.rivy.org/2014/04/install-a-kvm-host-on-ubuntu-14-04-trusty-tahr/")
and edited the the VM XML file as in this post [https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/1279176]("https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/1279176")

nothing.

```
**$ ip addr**

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:22:15:80:77:ad brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.111/24 brd 192.168.1.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::222:15ff:fe80:77ad/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 00:22:15:80:77:ae brd ff:ff:ff:ff:ff:ff
4: ovs-system: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default
    link/ether 72:dd:a2:82:68:6d brd ff:ff:ff:ff:ff:ff
5: ovsbr0: <BROADCAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN group default
    link/ether 56:67:f7:dc:97:43 brd ff:ff:ff:ff:ff:ff
    inet 172.16.11.1/24 brd 172.16.11.255 scope global ovsbr0
       valid_lft forever preferred_lft forever
    inet6 fe80::b8a5:c2ff:fe7d:453d/64 scope link
       valid_lft forever preferred_lft forever

```

```

**$ virsh net-list**
 Name                 State      Autostart     Persistent
----------------------------------------------------------
 ovsbr0               active     yes           yes


```

```

**$ sudo ovs-vsctl show**
3f253c6b-5a3f-479d-b13b-90459d4c3083
    Bridge "ovsbr0"
        Port "ovsbr0"
            Interface "ovsbr0"
                type: internal
    ovs_version: "2.0.1"


```

```

**$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:22:15:80:77:ad
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe80:77ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1982290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:947616 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2161705123 (2.1 GB)  TX bytes:990675980 (990.6 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:592335 errors:0 dropped:0 overruns:0 frame:0
          TX packets:592335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1067857236 (1.0 GB)  TX bytes:1067857236 (1.0 GB)

ovsbr0    Link encap:Ethernet  HWaddr 56:67:f7:dc:97:43
          inet addr:172.16.11.1  Bcast:172.16.11.255  Mask:255.255.255.0
          inet6 addr: fe80::5467:f7ff:fedc:9743/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:2590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:731384 (731.3 KB)  TX bytes:1944 (1.9 KB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:97:d0:54
          inet6 addr: fe80::fc54:ff:fe97:d054/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:21212 (21.2 KB)  TX bytes:648 (648.0 B)
```

---

### Post by kosmokramer314 on 2014-07-31
I have network connectivity on a new guest VM now.  I ended up taking Open vSwitch out of the equation by modifying /etc/network/interfaces on the host server and everything is working fine now.  Still need to remove Open vSwitch configuration though, but that is another story.

---

