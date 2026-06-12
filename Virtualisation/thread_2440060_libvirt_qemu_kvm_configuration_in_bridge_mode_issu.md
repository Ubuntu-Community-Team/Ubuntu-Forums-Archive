---
title: "libvirt qemu kvm configuration in bridge mode issue"
date: 2020-04-05
forum: Virtualisation
---

### Post by js.m on 2020-04-05
Hi Folks, 

I claiming for your help for  (What I think being a routing issue).
I've rebuild entirely my network everything work well but my guest VM's on my ubuntu server have no tnetwork access.

Network set-up:
[IMG]https://i.ibb.co/BGT4sJN/netwk.png[/IMG]


Current config:
tou
**HOST**:
```

server:~# ifconfig
bond0: flags=5187<UP,BROADCAST,RUNNING,MASTER,MULTICAST>  mtu 1500
        inet 192.168.1.200  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::a868:bff:fe60:c8da  prefixlen 64  scopeid 0x20<link>
        inet6 2a02:2788:174:4a:a868:bff:fe60:c8da  prefixlen 64  scopeid 0x0<global>
        inet6 2a02:2788:174:4a::2  prefixlen 128  scopeid 0x0<global>
        ether aa:68:0b:60:c8:da  txqueuelen 1000  (Ethernet)
        RX packets 32963  bytes 3574202 (3.5 MB)
        RX errors 0  dropped 270  overruns 0  frame 0
        TX packets 2459  bytes 283839 (283.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.201  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::8086:d0ff:fe52:2c28  prefixlen 64  scopeid 0x20<link>
        inet6 2a02:2788:174:4a::3  prefixlen 128  scopeid 0x0<global>
        inet6 2a02:2788:174:4a:8086:d0ff:fe52:2c28  prefixlen 64  scopeid 0x0<global>
        ether 82:86:d0:52:2c:28  txqueuelen 1000  (Ethernet)
        RX packets 16788  bytes 1905102 (1.9 MB)
        RX errors 0  dropped 270  overruns 0  frame 0
        TX packets 987  bytes 116786 (116.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether ac:22:0b:51:db:6c  txqueuelen 1000  (Ethernet)
        RX packets 120276  bytes 46682683 (46.6 MB)
        RX errors 0  dropped 1828  overruns 0  frame 0
        TX packets 7771  bytes 646405 (646.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf7f00000-f7f20000

enp1s0f0: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 1500
        ether aa:68:0b:60:c8:da  txqueuelen 1000  (Ethernet)
        RX packets 10258  bytes 1278865 (1.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2036  bytes 235007 (235.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xf7d80000-f7dfffff

enp1s0f1: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 1500
        ether aa:68:0b:60:c8:da  txqueuelen 1000  (Ethernet)
        RX packets 22705  bytes 2295337 (2.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 423  bytes 48832 (48.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xf7c80000-f7cfffff

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 75  bytes 7728 (7.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 75  bytes 7728 (7.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

vnet0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::fc54:ff:fef6:1ab1  prefixlen 64  scopeid 0x20<link>
        ether fe:54:00:f6:1a:b1  txqueuelen 1000  (Ethernet)
        RX packets 1161  bytes 92800 (92.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 22161  bytes 2428107 (2.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

vnet1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::fc54:ff:fe5e:4b97  prefixlen 64  scopeid 0x20<link>
        ether fe:54:00:5e:4b:97  txqueuelen 1000  (Ethernet)
        RX packets 1411  bytes 133698 (133.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 21546  bytes 2365676 (2.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

```

server:~$ ip route
default via 192.168.1.1 dev bond0 proto static
default via 192.168.1.1 dev br0 proto static
default via 192.168.68.1 dev br0 proto dhcp src 192.168.68.110 metric 100
192.168.1.0/24 dev bond0 proto kernel scope link src 192.168.1.200
192.168.1.0/24 dev br0 proto kernel scope link src 192.168.1.201
192.168.68.0/24 dev br0 proto kernel scope link src 192.168.68.110
192.168.68.1 dev br0 proto dhcp scope link src 192.168.68.110 metric 100

```

```
server:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 bond0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 br0
0.0.0.0         192.168.68.1    0.0.0.0         UG    100    0        0 br0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 bond0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
192.168.68.0    0.0.0.0         255.255.255.0   U     0      0        0 br0
192.168.68.1    0.0.0.0         255.255.255.255 UH    100    0        0 br0

```

virsh net-info host-bridge
Name:           host-bridge
UUID:           3e2315e4-7a64-44e6-b16f-c21111d4aca5
Active:         yes
Persistent:     yes
Autostart:      yes
Bridge:         br0

```
server:~# cat vm1.xml
<domain type='kvm'>
  <name>vm1</name>
  <uuid>f3b35552-154c-4560-a616-4f1c99903e8c</uuid>
  <memory unit='KiB'>2097152</memory>
  <currentMemory unit='KiB'>2097152</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <resource>
    <partition>/machine</partition>
  </resource>
  <os>
    <type arch='x86_64' machine='pc-i440fx-bionic'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
  </features>
  <cpu mode='custom' match='exact' check='full'>
    <model fallback='forbid'>Haswell-noTSX-IBRS</model>
    <feature policy='require' name='vme'/>
    <feature policy='require' name='f16c'/>
    <feature policy='require' name='rdrand'/>
    <feature policy='require' name='hypervisor'/>
    <feature policy='require' name='arat'/>
    <feature policy='require' name='xsaveopt'/>
    <feature policy='require' name='abm'/>
  </cpu>
  <clock offset='utc'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/kvm/images/bastion-ubuntu-bionical.qcow2'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hda' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x2'/>
    </controller>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='bridge'>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target type='isa-serial' port='0'>
        <model name='isa-serial'/>
      </target>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <input type='mouse' bus='ps2'/>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </memballoon>
  </devices>
  <seclabel type='dynamic' model='apparmor' relabel='yes'/>
  <seclabel type='dynamic' model='dac' relabel='yes'/>
</domain>

```

Does any one could help me to figure out what's wrong here?

Thanks ! :)

---

### Post by TheFu on 2020-04-05
Which release?
Please show the config files that control the host network setup.
When posting, please clearly show and label what is on the host and the quests. Don't make us guess.

Have you tried simplifying?  Remove the bond. Does that work?
The routes don't look correct. There should be only 1 route per subnet.

---

### Post by js.m on 2020-04-06
TheFu
Which release?
*Ubuntu 18.04 LTS*
Please show the config files that control the host network setup.
*cf below*
When posting, please clearly show and label what is on the host and the quests. Don't make us guess.
*Draw updated *
Have you tried simplifying?  Remove the bond. Does that work?
*I'll test it *
The routes don't look correct. There should be only 1 route per subnet.

Hi TheFu, 
First of all, thank for your answer

**HOST network cfg:**
```
server:~$ cat /etc/netplan/01-netcfg.yaml
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
 version: 2
 renderer: networkd
 ethernets:
  eno1:
    dhcp4: false
    dhcp6: false
  enp1s0f0:
    dhcp4: false
    dhcp6: false
    optional: true
  enp1s0f1:
    dhcp4: false
    dhcp6: false
    optional: true
 bonds:
  bond0:
   dhcp4: false
   dhcp6: false
   interfaces:
     - enp1s0f0
     - enp1s0f1
   addresses: [192.168.1.200/24]
   gateway4: 192.168.1.1
   nameservers:
     addresses: [1.1.1.1,1.0.0.1]
   optional: true
   parameters:
     mode: 802.3ad
     lacp-rate: fast
     mii-monitor-interval: 100
 bridges:
  br0:
   interfaces: [eno1]
   dhcp4: yes
   addresses: [192.168.1.201/24]
   gateway4: 192.168.1.1
   nameservers:
    addresses: [1.1.1.1,1.0.0.1]
   parameters:
    stp: true
    forward-delay: 4

```

My goal is to have both bond and br0 working in order to segregate traffic
br0 used from VM trafficn
bond0 used for host only traffic

---

### Post by TheFu on 2020-04-06
Question: How does the OS know which interface to use when they are on the same subnet, with the same routes, with the same metric?
Answer: It doesn't.

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 bond0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 br0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 bond0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
```

---

### Post by js.m on 2020-04-06
Indeed... -_-'  thanks to figured it out :)

---

