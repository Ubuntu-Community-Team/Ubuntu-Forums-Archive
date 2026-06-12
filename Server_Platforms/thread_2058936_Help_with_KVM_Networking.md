---
title: "Help with KVM Networking"
date: 2012-09-16
forum: Server Platforms
---

### Post by gonro952 on 2012-09-16
i simply cannot get the networking set up for KVM iv followed all the guides completely and multiple times and have done countless fresh installs. i followed this guide very througly and it has not worked for me. [http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-12.04-lts]("http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-12.04-lts")
iv also followed ubuntus tutorial on kvm and have had the exact same problem. these are all from fresh installs and the first thing iv tried to set up so nothing should be interfering. 
im just trying to get one vm running its nothing complicated but i cannot figure this out at all. 
when i try to ssh into the br0 device's ip address it just connects to the host. i can see that the vm is running just fine because of a screenshot through virsh, it shows the login in screen.

config for vm machine 
```
<domain type='kvm' id='1'>
  <name>vm1</name>
  <uuid>d71846b1-fb38-2d3a-cf07-7055b3f63416</uuid>
  <memory>4194304</memory>
  <currentMemory>4194304</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-1.0'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/vm1/ubuntu-kvm/tmpdxuJM6.qcow2'/>
      <target dev='hda' bus='ide'/>
      <alias name='ide0-0-0'/>
      <address type='drive' controller='0' bus='0' unit='0'/>
    </disk>
    <controller type='ide' index='0'>
      <alias name='ide0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:c8:xx:xx'/>
      <source bridge='br0'/>
      <target dev='vnet0'/>
      <model type='virtio'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='5900' autoport='yes' listen='127.0.0.1'>
      <listen type='address' address='127.0.0.1'/>
    </graphics>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
      <alias name='video0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <alias name='balloon0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </memballoon>
  </devices>
  <seclabel type='dynamic' model='apparmor' relabel='yes'>
    <label>libvirt-d71846b1-fb38-2d3a-cf07-7055b3f63416</label>
    <imagelabel>libvirt-d71846b1-fb38-2d3a-cf07-7055b3f63416</imagelabel>
  </seclabel>
</domain>
```

and network config

```
auto eth0
iface eth0 inet static
        address 172.29.xx.10
        netmask 255.255.255.0
        network 172.29.xx.0
        broadcast 172.29.xx.255
        gateway 172.29.xx.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8 8.8.4.4

auto br0
iface br0 inet static
        address 172.29.xx.11
        network 172.29.xx.0
        netmask 255.255.255.0
        broadcast 172.29.xx.255
        gateway 172.29.xx.1
        dns-nameservers 208.67.222.123
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```

is this a bad tutorial or something? any help would be greatly appreciated.

---

