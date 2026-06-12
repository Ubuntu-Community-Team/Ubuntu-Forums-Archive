---
title: "Network interface not raising on boot, despite auto in /etc/network/interfaces"
date: 2017-01-20
forum: Virtualisation
---

### Post by ads3 on 2017-01-20
I'm not sure if this belongs in Virtualization or Networking, as it involves both to an extent, but here goes. 

I have an Ethernet interface on my home server, interface ens6f0. This particular interface will be passed through to a libvirt-qemu-kvm virtual machine by means of SR-IOV. I'd like this VM to start a boot, so, naturally, I'd like the interface to come up at boot. So I've added this line to my /etc/network/interfaces file:

auto ens6f0

Just that line. It is not followed by "iface ens6f0 anything" because I do not want the host to configure the interface. I want the host to pull the interface up and pass it on to a VM. But this is where the issue starts. When I run "ip link" I can see the interface and the one it shares a NIC with just fine: ens6f0 and ens6f1 both show up, along with their virtual forwarders.  However, when I run "sudo ifup -a" (which is what runs at boot to parse /etc/network/interfaces and bring interfaces up) I get an error that reads, "Unknown interface ens6f0."

Huh?
I've confirmed the interface exists using ip link. How can it be unknown?

It gets better, though. If I run "sudo ifconfig ens6f0 up" it comes up just fine, without a fuss. 

Let me give you some insight into my system. Here's my /etc/network/interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# Intel NIC, wan interface, sr-iov passthrough to router vm
**auto ens6f0**

# The emergency backup network interface
auto enp4s0f0
iface enp4s0f0 inet dhcp

# lan bridge interface - host will get internet access through here once the router works
auto ovsbr0
allow-ovs ovsbr0
iface ovsbr0 inet static
        ovs_type OVSBridge
        address 10.0.0.2
        network 10.0.0.0
        netmask 255.255.255.0
        broadcast 10.0.0.255
        gateway 10.0.0.1
        dns-search ads103.sytes.net
        dns-nameservers 10.0.0.1 8.8.8.8 8.8.4.4
        ovs_ports ens6f1

# Intel NIC, lan interface, bridged
allow-ovsbr0 ens6f1
iface ens6f1 inet manual
        ovs_bridge ovsbr0
        ovs_type OVSPort

```

Here's $ ip link:
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp3s0f0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 80:c1:6e:24:05:4c brd ff:ff:ff:ff:ff:ff
3: enp3s0f1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 80:c1:6e:24:05:4e brd ff:ff:ff:ff:ff:ff
4: enp4s0f0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether 80:c1:6e:24:05:50 brd ff:ff:ff:ff:ff:ff
5: enp4s0f1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 80:c1:6e:24:05:52 brd ff:ff:ff:ff:ff:ff
**6: ens6f0: <NO-CARRIER,BROADCAST,MULTICAST,UP> **mtu 1500 qdisc mq state DOWN mode DEFAULT group default qlen 1000
    link/ether a0:36:9f:76:3a:b0 brd ff:ff:ff:ff:ff:ff
    vf 0 MAC 00:00:00:00:00:00, spoof checking on, link-state auto
    vf 1 MAC 00:00:00:00:00:00, spoof checking on, link-state auto
7: enp24s16f1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 4e:3f:78:a9:22:4f brd ff:ff:ff:ff:ff:ff
8: enp24s16f5: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 8a:66:97:0d:52:5c brd ff:ff:ff:ff:ff:ff
9: ens6f1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq master ovs-system state DOWN mode DEFAULT group default qlen 1000
    link/ether a0:36:9f:76:3a:b1 brd ff:ff:ff:ff:ff:ff
    vf 0 MAC 00:00:00:00:00:00, spoof checking on, link-state auto
    vf 1 MAC 00:00:00:00:00:00, spoof checking on, link-state auto
11: enp24s16f4: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether ca:e6:88:1e:de:58 brd ff:ff:ff:ff:ff:ff
12: ovs-system: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1
    link/ether 8e:40:f0:5d:9c:75 brd ff:ff:ff:ff:ff:ff
13: ovsbr0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/ether a0:36:9f:76:3a:b1 brd ff:ff:ff:ff:ff:ff
14: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default qlen 1000
    link/ether 52:54:00:81:eb:8e brd ff:ff:ff:ff:ff:ff
15: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast master virbr0 state DOWN mode DEFAULT group default qlen 1000
    link/ether 52:54:00:81:eb:8e brd ff:ff:ff:ff:ff:ff
16: enp24s16: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether f6:bd:4a:ad:b2:f4 brd ff:ff:ff:ff:ff:ff

```

Additionally, here's my libvirt xml config for passing this interface through to a VM:
```
 <interface type='hostdev' managed='yes'>
      <mac address='52:54:00:3c:82:d2'/>
      <source>
        <address type='pci' domain='0x0000' bus='0x18' slot='0x10' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </interface>
```

Also, totally off topic, but do we have one of those "Spoiler" buttons on this forum? That's quite a bit of text, and I'd love to be able to hide it away. I tried the bbcode [showhide] and [spoiler] but those didn't work.

---

### Post by wildmanne39 on 2017-01-20
*Thread moved to **Virtualisation**.*

---

### Post by ads3 on 2017-01-29
If y'all don't mind, I'd like to bump this post. I understand that community support isn't guaranteed, but it seems odd that this hasn't been looked at a lot in a week. There hasn't been any change in behavior, but I haven't done a whole lot more tinkering since I was at my wits end when I made the post. :)

---

### Post by robstarusa2 on 2017-02-14
I have EXACTLY the same problem.  I'm not even doing briding, openvswitch etc.  Every time my machine boots, the vms are useless until I manually "ifconfig enp2s0f0 up" and then they all just start working. I have "auto enp2s0f0" in my /etc/network/interfaces file but it seems to be ignored/not processed.  Manually runing "ifdown enp2s0f0" and "ifup enp2s0f0" doesn't return an error, but also doesn't work...

---

### Post by heiko_s on 2017-02-15
For one thing I assume the Network Manager - if available - has been disabled (I'm currently on Linux Mint, which is based on Ubuntu), else the /etc/network/interfaces file won't be evaluated.

In my setup I have a rather simple interfaces file that does the job:
```
auto lo
iface lo inet loopback

auto br0

iface br0 inet static
address 192.168.0.110
broadcast 192.168.0.255
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.8.8
bridge_ports eth0
bridge_stp off

```

The NIC is specified under the bridge configuration with bridge_ports eth0 (replace with your interface name, I'm still using the old names).

Obviously the above example defines a bridged network with static IPs. It's easy to switch to DHCP.

Unfortunately I'm not familiar with SR-IOV (I still use tap with vhost=on), except for having seen some nice slideware. If you have a dedicated NIC, why not pass it through using PCI passthrough?

EDIT: It took me a moment to realize you are using Openswitch. In that case I'm not sure what I wrote is relevant - it's you to decide as I'm not acquainted with Openswitch.

---

