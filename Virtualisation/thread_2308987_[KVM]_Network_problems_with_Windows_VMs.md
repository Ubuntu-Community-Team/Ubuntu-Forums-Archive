---
title: "[KVM] Network problems with Windows VMs"
date: 2016-01-07
forum: Virtualisation
---

### Post by jack_brennan2 on 2016-01-07
Hi,

I've been running KVM on Ubuntu 14.04.3 for quite some time and all my VMs have been Ubuntu 14.04.3 VMs. They run perfectly!

Last night I had to setup a Windows VM for an application that requires the MSSQL/IIS/Windows Server stack. I created a Windows Server 2012 R2 VM and everything went fine - the machine is also very snappy. But network connectivity is a problem.

The following works:
1. Ping hosts on same subnet and internet
2. Telnet to hosts on same subnet and internet

Everything else network related doesn't work. Browsing, Windows update, network shares ect...

The VM is connected to the same bridged network adapter as the other VMs on the server. I've also tried with both the E1000 network adapter type and VirtIO with updates drivers.

I haven't actually used any Windows machines on KVM before, so maybe there is something that needs to be done on the host to accommodate a Windows VM?

Appreciate any help on the matter.


**XMLDump of VM**
```
<domain type='kvm'>
  <name>test-windows</name>
  <uuid>3136de3b-6e3b-4f76-748f-2bb13d373f42</uuid>
  <memory unit='KiB'>2097152</memory>
  <currentMemory unit='KiB'>2097152</currentMemory>
  <vcpu placement='static'>2</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>SandyBridge</model>
    <vendor>Intel</vendor>
    <feature policy='require' name='vme'/>
    <feature policy='require' name='dtes64'/>
    <feature policy='require' name='invpcid'/>
    <feature policy='require' name='vmx'/>
    <feature policy='require' name='erms'/>
    <feature policy='require' name='xtpr'/>
    <feature policy='require' name='smep'/>
    <feature policy='require' name='pbe'/>
    <feature policy='require' name='est'/>
    <feature policy='require' name='monitor'/>
    <feature policy='require' name='abm'/>
    <feature policy='require' name='tm'/>
    <feature policy='require' name='acpi'/>
    <feature policy='require' name='fma'/>
    <feature policy='require' name='osxsave'/>
    <feature policy='require' name='ht'/>
    <feature policy='require' name='pdcm'/>
    <feature policy='require' name='pdpe1gb'/>
    <feature policy='require' name='fsgsbase'/>
    <feature policy='require' name='f16c'/>
    <feature policy='require' name='ds'/>
    <feature policy='require' name='tm2'/>
    <feature policy='require' name='avx2'/>
    <feature policy='require' name='ss'/>
    <feature policy='require' name='bmi1'/>
    <feature policy='require' name='bmi2'/>
    <feature policy='require' name='pcid'/>
    <feature policy='require' name='ds_cpl'/>
    <feature policy='require' name='movbe'/>
    <feature policy='require' name='rdrand'/>
  </cpu>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/p-sn-ss-01.qcow2'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hda' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
<source file='/var/lib/libvirt/iso/virtio-win-0.1.112.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='1' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:93:31:21'/>
      <source bridge='vm_network'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <interface type='bridge'>
      <mac address='52:54:00:03:ab:36'/>
      <source bridge='vm_network'/>
      <model type='e1000'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'/>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='vga' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </memballoon>
  </devices>
</domain>

```

Bridged NIC on host
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet static
        address 10.1.4.3
        netmask 255.255.255.0
        gateway 10.1.4.1
        dns-nameservers 10.1.4.1
auto vm_network
iface vm_network inet dhcp
   bridge_ports eth0
   bridge_stp on
   bridge_fd 0
   bridge_maxwait  0

```

---

### Post by MAFoElffen on 2016-01-07
In the Windows Server 2012R2 setup, I use all three: Virtio SCSI, Virtio Network and the Virtio memory balloon drivers. 

The KVM virtio driver ISOs for Ubuntu are located [here]("https://launchpad.net/kvm-guest-drivers-windows/+download")

---

### Post by jack_brennan2 on 2016-01-07
> **MAFoElffen said:**
> In the Windows Server 2012R2 setup, I use all three: Virtio SCSI, Virtio Network and the Virtio memory balloon drivers. 

The KVM virtio driver ISOs for Ubuntu are located [here]("https://launchpad.net/kvm-guest-drivers-windows/+download")
Hi, thanks for that.
Although I did have the drivers installed. So that wasn't the problem. However the problem was still related to the drivers :)

A friend of mine did find the problem.

The drivers in Windows set an unusually high MTU value which was causing the problems.
[http://blogs.technet.com/b/askpfeplat/archive/2014/12/01/psa-incorrect-mtu-size-causes-connectivity-issues-with-windows-server-2012-and-windows-server-2012-r2.aspx](http://blogs.technet.com/b/askpfeplat/archive/2014/12/01/psa-incorrect-mtu-size-causes-connectivity-issues-with-windows-server-2012-and-windows-server-2012-r2.aspx)

Once that was lowered everything started to work as expected.

---

