---
title: "Create a wireless bridge for KVM using parprouted"
date: 2010-01-09
forum: Virtualisation
---

### Post by jimezam on 2010-01-09
I want to create a bridge using a wireless interface to communicate my KVM machines.  As I read, its not possible to make it using a wireless. So I am trying to use the parprouted alternative but its not working for me.

This is what I am doing in the VMs server.

$ sudo /usr/sbin/tunctl -t tap0 -u jimezam
$ sudo /sbin/ip link set tap0 up
$ sudo /sbin/ip addr add 192.168.1.100/24 dev tap0
$ sudo /usr/sbin/parprouted wlan0 tap0
$ sudo sysctl net.ipv4.ip_forward=1

On the guest OS I specified an static address, DNS and gateway.

$ cat /etc/network/interfaces

auto eth0
iface eth0 inet static
        address 192.168.1.101
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.100

On the VM specification I set the network as a bridge.

$ cat /etc/libvirt/qemu/vm.xml

    <interface type='bridge'>
      <source bridge='tap0'/>
    </interface>

When the VM goes up it has the address (because its static) but no networking is available.

I found a lot of examples with VirtualBox but I haven't been successfully adapting them to KVM/LibVirt.

Please help me.

jimezam.

---

