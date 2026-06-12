---
title: "how to update the Network adapter in Windows XP Guest OS - Ubuntu 16.04 KVM."
date: 2019-07-20
forum: Virtualisation
---

### Post by dhanesh2019 on 2019-07-20
Hi Everyone, 

I have WindowsXP.qcow2 image which is running in our old rack server still & assigned with public IP. 

Now am setting up the Same WindowsXP.qcow2 image with new Rack Server with Ubuntu 16.04 KVM. 

I can able to start the VM with WindowsXP.qcow2 image the machine came working fine. 

But ethernet interface is not available I have checked the device manager in WindowsXP guest via VNC viewer the Ethernet driver is not available. 

How to fix this and below is the domain xml file for your kind reference. 

My Host Machine Network Details 

eth0 / br0 Configured with Public IP 

eth1 / br1 Configured with private, WindowsXP need to work with private network only. 

Please help advance thank you... 

```
<domain type='kvm' id='9'>  <name>windows-xp</name>
  <uuid>ID</uuid>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>4194304</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <resource>
    <partition>/machine</partition>
  </resource>
  <os>
    <type arch='x86_64' machine='pc-i440fx-xenial'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
    </hyperv>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Broadwell-IBRS</model>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='yes'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/RootPartitions/backup/windows20190717.qcow2'/>
      <backingStore/>
      <target dev='hda' bus='ide'/>
      <alias name='ide0-0-0'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <alias name='usb'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <alias name='usb'/>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <alias name='usb'/>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <alias name='usb'/>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'>
      <alias name='pci.0'/>
    </controller>
    <controller type='ide' index='0'>
      <alias name='ide'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='bridge'>
      <mac address='34:54:03:ef:e8:a9'/>
      <source network='default' bridge='br1'/>
      <target dev='vnet1'/>
      <model type='virtio'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <source path='/dev/pts/2'/>
      <target port='0'/>
      <alias name='serial0'/>
    </serial>
    <console type='pty' tty='/dev/pts/2'>
      <source path='/dev/pts/2'/>
      <target type='serial' port='0'/>
      <alias name='serial0'/>
    </console>
    <input type='tablet' bus='usb'>
      <alias name='input0'/>
    </input>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='5901' autoport='yes' listen='127.0.0.1'>
      <listen type='address' address='127.0.0.1'/>
    </graphics>
    <video>
      <model type='vga' vram='16384' heads='1'/>
      <alias name='video0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <alias name='balloon0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </memballoon>
  </devices>
  <seclabel type='dynamic' model='apparmor' relabel='yes'>
    <label>libvirt-8dad9b47-7ea7-4ec8-a56b-af941227effe</label>
    <imagelabel>libvirt-8dad9b47-7ea7-4ec8-a56b-af941227effe</imagelabel>
  </seclabel>
</domain>

```

[ATTACH=CONFIG]283642[/ATTACH]

---

### Post by TheFu on 2019-07-20
The networking is controlled by the bridge for outside stuff and inside the OS for everything else.
The only part of network settings controlled by the qemu xml VM settings is which bridge is used and which network device is used.

 If there are WinXP virtio drivers, you can use this, but they also must be manually installed.
```
      <model type='virtio'/>
```
I have doubts whether you can find those for WinXP today, but I didn't look.  Using virtio should be better, in theory.

BTW, with WinXP, it would be best to install the Intel PRO/1000 NIC drivers from Intel and use those for the virtual device. Here's why: [https://blog.jdpfu.com/2010/06/22/virtualbox-performance-improved](https://blog.jdpfu.com/2010/06/22/virtualbox-performance-improved)  The article is for Vbox, but applies to KVM/QEMU as well. 

WinXP wasn't shipped with support for many devices we all take for granted today.  SATA, GigE, Virtio .... so to use those, each needs to be manually installed.  BTW, if the XP machine ever has problems booting, you'll need to remember this, since the recovery mode setup doesn't use manually installed drivers.  Basically, the SATA disk (I would switch to that too, BTW), won't be seen.

---

