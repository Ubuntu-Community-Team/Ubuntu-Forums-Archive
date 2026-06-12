---
title: "VM deployed by virt-manager does not get the ip address automatically"
date: 2010-11-28
forum: Virtualisation
---

### Post by swamybabu on 2010-11-28
Hi,

Can someone help me on the following issue?

Setup Info:
=======

* ubuntu 10.10 x86_64
* kvm
* virt-manager

- Deployed WinXP VM using virt-manager (virtualization type : kvm)
- My VM is not getting ip address (n/w : 192.168.0.0) automatically. Can someone help me on this?

I appreciate if someone can provide me any tutorial links that talks about manually deploying VMs using /usr/bin/kvm (not through virt-manager).

[COLOR=Sienna]cat /etc/network/interface

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto br0
iface br0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxwait 0
        bridge_maxage 12
        bridge_stp off
[/COLOR]
[COLOR=Olive]cat /etc/libvirt/qemu/WinXP.xml [network properties snippet]

 <interface type='bridge'>
      <mac address='52:54:00:92:d9:12'/>
      <source bridge='br0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <interface type='bridge'>
      <mac address='52:54:00:c8:6e:83'/>
      <source bridge='br0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </interface>[/COLOR]

[COLOR=Green]ps -aef | grep -i kvm (output is truncated and contains only network info)

/usr/bin/kvm  -device rtl8139,vlan=0,id=net0,mac=52:54:00:92:d9:12,bus=pci.0,addr=0x3 -net tap,fd=47,vlan=0,name=hostnet0 -device rtl8139,vlan=1,id=net1,mac=52:54:00:c8:6e:83,bus=pci.0,addr=0x6 -net tap,fd=48,vlan=1,name=hostnet1 
[/COLOR]

---

### Post by gdahlm on 2010-11-28
try removing the dhcp address from the bridge interface


e.g. iface eth0 inet manual

---

