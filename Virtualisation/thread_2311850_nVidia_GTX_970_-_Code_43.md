---
title: "nVidia GTX 970 - Code 43"
date: 2016-01-30
forum: Virtualisation
---

### Post by KillerKelvUK on 2016-01-30
Have a working GTX 650 using VFIO + Win10...upgraded the 650 for a 970...did the whole driver dance for uninstall/clean/reinstall...now I'm getting code 43!

Domain XML below, anyone any ideas?

Thanks.

```
<domain type='kvm'>  <name>blackwindows</name>
  <uuid>36487720-7a12-4732-ae3e-969e13188bd8</uuid>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <memoryBacking>
    <hugepages/>
  </memoryBacking>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-q35-2.5'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/qemu/OVMF.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/blackwindows_VARS.fd</nvram>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <kvm>
      <hidden state='on'/>
    </kvm>
    <vmport state='off'/>
  </features>
  <cpu mode='host-model'>
    <model fallback='allow'/>
    <topology sockets='1' cores='2' threads='2'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
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
      <source file='/mnt/vms/blackwindows.qcow2'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x04' function='0x0'/>
    </disk>
    <controller type='sata' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1f' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pcie-root'/>
    <controller type='pci' index='1' model='dmi-to-pci-bridge'>
      <model name='i82801b11-bridge'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1e' function='0x0'/>
    </controller>
    <controller type='pci' index='2' model='pci-bridge'>
      <model name='pci-bridge'/>
      <target chassisNr='2'/>
      <address type='pci' domain='0x0000' bus='0x01' slot='0x01' function='0x0'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x03' function='0x0'/>
    </controller>
    <controller type='usb' index='0' model='nec-xhci'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x02' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:88:2a:0a'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x01' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x06' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x07' function='0x0'/>
    </hostdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x05' function='0x0'/>
    </memballoon>
  </devices>
</domain>

```

---

### Post by KillerKelvUK on 2016-01-31
Little embarrassing but erm seems like a code 43 can also be caused by a dodgy PCIe power cable/connector...threw me for a loop thinking it was a driver-->kvm issue.  Would be nice if Asus actually published a manual that described that the LED indicator will be red if there is a problem and white if all okay.

Suffice to say 650 to 970 upgrade working and would have been seamless if not for the PBKC issue :-)

---

### Post by Habitual on 2016-01-31
Good job and well done!

---

