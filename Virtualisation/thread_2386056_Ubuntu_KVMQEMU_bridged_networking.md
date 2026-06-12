---
title: "Ubuntu KVM/QEMU bridged networking"
date: 2018-02-28
forum: Virtualisation
---

### Post by mpmackenna on 2018-02-28
I am having trouble getting bridged networking to work in KVM on Ubuntu 16.04. I installed kvm and I am using a combination of virt-manager and virsh to configure guests. I am able to install and configure quests and if I install to default NAT network everything works as expected. I have Ubuntu 16.04 installed on an HP Proliant 370 G6 with a NIC with 4 one gigabit ports and I installed two guests one is Windows 10 and the other is Debian 9. My experience in the past is with VMware ESXi. I have NIC port 0 configured as the host network port. I would like to configure the other three to be shared among guests. Whenever I configure a bridge interface and then assign the interface to a VM the VM fails to get an IP over DHCP.
Here is my output of ip add sh on the host
```

root@hpkvm1 09:57:59 0 :/var/lib/libvirt $ ip add sh
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: ens10f0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether d8:d3:85:d8:af:6c brd ff:ff:ff:ff:ff:ff
    inet 10.8.2.10/16 brd 10.8.255.255 scope global ens10f0
       valid_lft forever preferred_lft forever
    inet6 fe80::dad3:85ff:fed8:af6c/64 scope link
       valid_lft forever preferred_lft forever
3: ens10f1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UP group default qlen 1000
    link/ether d8:d3:85:d8:af:6d brd ff:ff:ff:ff:ff:ff
4: ens10f2: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether d8:d3:85:d8:af:6e brd ff:ff:ff:ff:ff:ff
5: ens10f3: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether d8:d3:85:d8:af:6f brd ff:ff:ff:ff:ff:ff
7: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default
    link/ether 02:42:a4:92:65:c6 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 scope global docker0
       valid_lft forever preferred_lft forever
8: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:b0:99:17 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
9: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast master virbr0 state DOWN group default qlen 1000
    link/ether 52:54:00:b0:99:17 brd ff:ff:ff:ff:ff:ff
13: tap0: <NO-CARRIER,BROADCAST,MULTICAST,PROMISC,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 16:e1:3e:a8:28:b5 brd ff:ff:ff:ff:ff:ff
15: macvtap0@ens10f0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 500
    link/ether 52:54:00:74:61:91 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::5054:ff:fe74:6191/64 scope link
       valid_lft forever preferred_lft forever
16: virbr1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:5e:a6:92 brd ff:ff:ff:ff:ff:ff
    inet 192.168.86.1/24 brd 192.168.86.255 scope global virbr1
       valid_lft forever preferred_lft forever
17: virbr1-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast master virbr1 state DOWN group default qlen 1000
    link/ether 52:54:00:5e:a6:92 brd ff:ff:ff:ff:ff:ff
21: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether d8:d3:85:d8:af:6d brd ff:ff:ff:ff:ff:ff
    inet 10.8.51.158/16 brd 10.8.255.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fe80::dad3:85ff:fed8:af6d/64 scope link
       valid_lft forever preferred_lft forever
23: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:9c:94:a9 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fe9c:94a9/64 scope link
       valid_lft forever preferred_lft forever
root@hpkvm1 10:08:23 0 :/var/lib/libvirt $

```
Here is the network section of the virsh dumpxml config for my Debian 9 guest
```

    <interface type='bridge'>
      <mac address='52:54:00:9c:94:a9'/>
      <source bridge='br0'/>
      <target dev='vnet0'/>
      <model type='virtio'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>

```

When the guest boots, it shows the interface is up but it doesn't get an IP from DHCP. The br0 interface on the host was able to obtain an IP from DHCP. I would like these VMs to receive IPs from DHCP and respond to network requests as if they are physical machines on the same network as the host. What am I missing in my configuration? Thanks.

---

### Post by Doug S on 2018-02-28
> **mpmackenna said:**
> ...
Here is the network section of the virsh dumpxml config for my Debian 9 guest
```

    <interface type='bridge'>
      <mac address='52:54:00:9c:94:a9'/>
      <source bridge='br0'/>
      <target dev='vnet0'/>
      <model type='virtio'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>

```
I am not sure, but I think "vnet0" might be a problem. Here is the same area from one of my VM's:```
    <interface type='bridge'>
      <mac address='52:54:00:27:1b:9e'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>

```And here is the command I used to create the VM:```
sudo virt-install -n serv64_dev -r 8192 --disk path=/media/vm/serv64_dev.img,bus=virtio,size=50 -c bionic-server-amd64-20180227.iso [COLOR="#FF0000"]--network bridge=br0,model=virtio,mac=52:54:00:27:1b:9e[/COLOR] --video=vmvga --graphics vnc,listen=0.0.0.0 --noautoconsole -v --vcpus=4

```

---

### Post by TheFu on 2018-03-14
Did you manually create a bridge either using brctl or some stanzas in the /etc/network/interface file? 
I would create a different bridge device for each NIC port, but I suppose you could bond those ports into a single device if your network infrastructure supports bonding.

For example, 
```
$ brctl show
bridge name     bridge id               STP enabled     interfaces
br0             8000.80ee7307ccb6       no              eth0
br1             8000.80ee7307ccb7       no              eth1

```
I set eth0 to be manually started ... and tell the bridge to use eth0 for the bridge used by VMs.
I do not use NAT setups.

---

