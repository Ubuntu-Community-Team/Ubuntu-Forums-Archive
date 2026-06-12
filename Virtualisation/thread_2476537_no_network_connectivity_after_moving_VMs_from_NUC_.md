---
title: "no network connectivity after moving VMs from NUC 10 to NUC 11"
date: 2022-06-29
forum: Virtualisation
---

### Post by glc650 on 2022-06-29
I've got two VMs that were created (virt-install) on an Intel NUC 10 i5.  I would now like to move them to a NUC 11 i7.  Both NUCs are configured the same  software-wise (Ubuntu 20.04.4 Server with related virt/kvm/qem packages).

When I start either VM on the NUC 11 I get no network connectivity unless I use the default vrbr.

NUC 10 netplan:
```

# This is the network config written by 'subiquity'
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: false
  vlans:
    eno1.100:
      dhcp4: false
      id: 100
      link: eno1
    eno1.101:
      dhcp4: false
      id: 101
      link: eno1
  bridges:
    br0.100:
      interfaces: [eno1.100]
      dhcp4: false
      addresses: [10.0.0.9/24]
      routes:
        - to: default
          via: 10.0.0.254
      nameservers:
        addresses: [1.1.1.1,1.0.0.1]
    br0.101:
      interfaces: [eno1.101]
      dhcp4: false
      addresses: [10.1.0.9/24]
      nameservers:
        addresses: [1.1.1.1,1.0.0.1]
```


NUC 11 netplan:
```

# This is the network config written by 'subiquity'
network:
  version: 2
  renderer: networkd
  ethernets:
    enp87s0:
      dhcp4: false
  vlans:
    enp87s0.100:
      dhcp4: false
      id: 100
      link: enp87s0
    enp87s0.101:
      dhcp4: false
      id: 101
      link: enp87s0
  bridges:
    br0.100:
      interfaces: [enp87s0.100]
      dhcp4: false
      addresses: [10.0.0.3/24]
      routes:
        - to: default
          via: 10.0.0.254
      nameservers:
        addresses: [1.1.1.1,1.0.0.1]
    br0.101:
      interfaces: [enp87s0.101]
      dhcp4: false
      addresses: [10.1.0.3/24]
      nameservers:
        addresses: [1.1.1.1,1.0.0.1]

```

Same config aside from interface names and IPs.

vm bridge #1:
```

<network>
  <name>br0.100</name>
  <uuid>a0847f3a-c333-4d20-b418-a7ca2f2b9baa</uuid>
  <forward mode='bridge'/>
  <bridge name='br0.100'/>
</network>

```

vm #1 xml:
```
<domain type='kvm'>
  <name>server-vmpc</name>
  <uuid>1781be34-c9bb-4ee4-8e96-f0c10a61baca</uuid>
  <metadata>
    <libosinfo:libosinfo xmlns:libosinfo="http://libosinfo.org/xmlns/libvirt/domain/1.0">
      <libosinfo:os id="http://ubuntu.com/ubuntu/20.04"/>
    </libosinfo:libosinfo>
  </metadata>
  <memory unit='KiB'>6291456</memory>
  <currentMemory unit='KiB'>6291456</currentMemory>
  <vcpu placement='static'>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-q35-4.2'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
  </features>
  <cpu mode='custom' match='exact' check='full'>
    <model fallback='forbid'>Broadwell-noTSX-IBRS</model>
    <feature policy='require' name='ibpb'/>
    <feature policy='require' name='md-clear'/>
    <feature policy='require' name='spec-ctrl'/>
    <feature policy='require' name='ssbd'/>
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
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/server-vmpc.qcow2'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x03' slot='0x00' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='sda' bus='sata'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x2'/>
    </controller>
    <controller type='sata' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1f' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pcie-root'/>
    <controller type='pci' index='1' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='1' port='0x8'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x0' multifunction='on'/>
    </controller>
    <controller type='pci' index='2' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='2' port='0x9'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='pci' index='3' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='3' port='0xa'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='4' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='4' port='0xb'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x3'/>
    </controller>
    <controller type='pci' index='5' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='5' port='0xc'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x4'/>
    </controller>
    <controller type='pci' index='6' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='6' port='0xd'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x5'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x00' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='00:0c:29:c5:57:c3'/>
      <source bridge='br0.100'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target type='isa-serial' port='0'>
        <model name='isa-serial'/>
      </target>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='unix'>
      <target type='virtio' name='org.qemu.guest_agent.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x04' slot='0x00' function='0x0'/>
    </memballoon>
    <rng model='virtio'>
      <backend model='random'>/dev/urandom</backend>
      <address type='pci' domain='0x0000' bus='0x05' slot='0x00' function='0x0'/>
    </rng>
  </devices>
</domain>

```

vm bridge #2:
```

<network>
  <name>br0.101</name>
  <uuid>0d1a4524-2095-4eaf-b27c-8055c1eab371</uuid>
  <forward mode='bridge'/>
  <bridge name='br0.101'/>
</network>

```

vm #2 xml:
```

<domain type='kvm'>
  <name>server-vmpc2</name>
  <uuid>aec36798-5a12-4d51-b17c-58ee96874d76</uuid>
  <metadata>
    <libosinfo:libosinfo xmlns:libosinfo="http://libosinfo.org/xmlns/libvirt/domain/1.0">
      <libosinfo:os id="http://ubuntu.com/ubuntu/20.04"/>
    </libosinfo:libosinfo>
  </metadata>
  <memory unit='KiB'>6291456</memory>
  <currentMemory unit='KiB'>6291456</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-q35-4.2'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
  </features>
  <cpu mode='custom' match='exact' check='full'>
    <model fallback='forbid'>Broadwell-noTSX-IBRS</model>
    <feature policy='require' name='ibpb'/>
    <feature policy='require' name='md-clear'/>
    <feature policy='require' name='spec-ctrl'/>
    <feature policy='require' name='ssbd'/>
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
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/server-vmpc2.qcow2'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x03' slot='0x00' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='sda' bus='sata'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x2'/>
    </controller>
    <controller type='sata' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1f' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pcie-root'/>
    <controller type='pci' index='1' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='1' port='0x8'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x0' multifunction='on'/>
    </controller>
    <controller type='pci' index='2' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='2' port='0x9'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='pci' index='3' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='3' port='0xa'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='4' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='4' port='0xb'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x3'/>
    </controller>
    <controller type='pci' index='5' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='5' port='0xc'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x4'/>
    </controller>
    <controller type='pci' index='6' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='6' port='0xd'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x5'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x00' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='00:50:56:29:4f:46'/>
      <source bridge='br0.101'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target type='isa-serial' port='0'>
        <model name='isa-serial'/>
      </target>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='unix'>
      <target type='virtio' name='org.qemu.guest_agent.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x04' slot='0x00' function='0x0'/>
    </memballoon>
    <rng model='virtio'>
      <backend model='random'>/dev/urandom</backend>
      <address type='pci' domain='0x0000' bus='0x05' slot='0x00' function='0x0'/>
    </rng>
  </devices>
</domain>

```

I tried changing <model type='virtio'/> to e1000 but that didn't help.

vm 1 & 2 netplan:
```

# This is the network config written by 'subiquity'
network:
  ethernets:
    enp1s0:
      dhcp4: false
  version: 2

```

---

### Post by Doug S on 2022-06-29
What kernel is your host running and what model number is the i7 (and the i5 for that matter)? It is a long shot, but I had to enable the HWE stuff and move to more recent kernels than 5.4 series when I got a i5-10600K, otherwise the VM's bridged networks did not work. The configuration was fine.  Your configuration is different, but maybe.

References:
[https://ubuntuforums.org/showthread.php?t=2461631]("https://ubuntuforums.org/showthread.php?t=2461631")
[https://askubuntu.com/questions/1333453/bridged-networking-in-kvm-qemu-lan-addressed-packets-dropped]("https://askubuntu.com/questions/1333453/bridged-networking-in-kvm-qemu-lan-addressed-packets-dropped")

---

### Post by glc650 on 2022-06-29
Everything is running 5.4.0-121
NUC10i5FNH, NUC11PAHi7

---

### Post by glc650 on 2022-06-29
> **Doug S said:**
>  I had to enable the HWE stuffThat did  the trick.  I then decided to try 22.04 server (5.15.0-40-generic) and  that works as well so I think that is where I will stay put.

> **Doug S said:**
>  Your configuration is different, Different how?

---

### Post by Doug S on 2022-06-29
Glad my "long shot" suggestion actually helped. Thanks for reporting back, as most don't.

Your configuration differs from mine in that I use just one host bridge for all my VM's. I also don't understand your VM's netplan file, but don't really want to dig into it right now.

```
doug@s19:~$ brctl show
bridge name     bridge id               STP enabled     interfaces
br0             8000.3c7c3f0d9983       no              enp3s0
                                                        vnet0
                                                        vnet1
                                                        vnet2

doug@s19:~$ virsh list --all
 Id   Name      State
--------------------------
 1    desk-ff   running
 2    desk-hh   running
 3    desk-ii   running
 -    serv-xx   shut off

doug@s19:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP group default qlen 1000
    link/ether 3c:7c:3f:0d:99:83 brd ff:ff:ff:ff:ff:ff
3: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 3c:7c:3f:0d:99:83 brd ff:ff:ff:ff:ff:ff
    inet 192.168.111.136/24 brd 192.168.111.255 scope global dynamic br0
       valid_lft 55083sec preferred_lft 55083sec
4: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:22:2f:dc brd ff:ff:ff:ff:ff:ff
5: vnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:60:ea:3e brd ff:ff:ff:ff:ff:ff
6: vnet2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:60:ea:5e brd ff:ff:ff:ff:ff:ff


```

---

### Post by glc650 on 2022-06-29
```
server@server-pc:~$ brctl show
bridge name    bridge id        STP enabled    interfaces
br0.100        8000.f600d01aeacd    no        enp87s0.100
                            vnet0
br0.101        8000.8a37143b7dc6    no        enp87s0.101
                            vnet1
                            vnet9
virbr0        8000.52540081da05    yes
server@server-pc:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: enp87s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 88:ae:dd:01:60:2d brd ff:ff:ff:ff:ff:ff
3: br0.100: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether f6:00:d0:1a:ea:cd brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.3/24 brd 10.0.0.255 scope global br0.100
       valid_lft forever preferred_lft forever
4: br0.101: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 8a:37:14:3b:7d:c6 brd ff:ff:ff:ff:ff:ff
    inet 10.1.0.3/24 brd 10.1.0.255 scope global br0.101
       valid_lft forever preferred_lft forever
5: enp87s0.101@enp87s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br0.101 state UP group default qlen 1000
    link/ether 88:ae:dd:01:60:2d brd ff:ff:ff:ff:ff:ff
6: enp87s0.100@enp87s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br0.100 state UP group default qlen 1000
    link/ether 88:ae:dd:01:60:2d brd ff:ff:ff:ff:ff:ff
7: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:81:da:05 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
8: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br0.100 state UNKNOWN group default qlen 1000
    link/ether fe:0c:29:c5:57:c3 brd ff:ff:ff:ff:ff:ff
9: vnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br0.101 state UNKNOWN group default qlen 1000
    link/ether fe:50:56:29:4f:46 brd ff:ff:ff:ff:ff:ff
17: vnet9: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br0.101 state UNKNOWN group default qlen 1000
    link/ether fe:50:56:32:d5:eb brd ff:ff:ff:ff:ff:ff
server@server-pc:~$
```

```
server@server-pc:~$ virsh list --all
 Id   Name           State
------------------------------
 1    server-vmpc    running
 2    server-vmpc2   running
 10   roon-vmpc      running
server@server-pc:~$
```


I have my third VM up now.  Two of my VMs need to be on my 10.1.0.0/24 subnet so I use one bridge to do that and the other bridge is used to put a VM on my 10.0.0.0/24 subnet.  I don't use the default bridge.

```
server@server-pc:~$ virsh net-list --all
 Name      State    Autostart   Persistent
--------------------------------------------
 br0.100   active   yes         yes
 br0.101   active   yes         yes
 default   active   yes         yes

server@server-pc:~$
```

---

