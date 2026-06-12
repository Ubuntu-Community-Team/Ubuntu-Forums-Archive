---
title: "KVM guest causes host to kernel panic"
date: 2011-05-03
forum: Virtualisation
---

### Post by SergeiFranco on 2011-05-03
Hi, I am facing this very annoying problem: I get repeatable kernel panic on KVM Host.

The panic is very difficult to catch as most of the time it is not even responding to Ctr+Alt+SysReq combos.

The last error is: "Fixing recursive fault but reboot is needed!"

The host:
Ubuntu natty (server install)
2.6.38-8-generic i686
running software mdadm raid1 (multiple of that).
Core2Duo E6300
2GB RAM
The guest:
Ubuntu natty (server install)
2.6.38-8-generic i686
Bridge mode networking
512MB RAM
```
<domain type='kvm'>
  <name>deluge</name>
  <uuid>de900b25-6dc3-cfd6-4fb1-55c6f9755b00</uuid>
  <memory>524288</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='i686' machine='pc-0.14'>hvm</type>
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
      <source file='/var/lib/libvirt/images/deluge.qcow2'/>
      <target dev='hda' bus='ide'/>
      <address type='drive' controller='0' bus='0' unit='0'/>
    </disk>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:8b:63:6e'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' listen='127.0.0.1'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```

---

### Post by SergeiFranco on 2011-05-04
Originally I believed it was raid resync that affected frequency of the panic, but I waited for resync to finish and started machine, which caused host to panic within 15 min.

Perhaps I should ditch kvm in favour of either virtual box, vmware or xen... 

I am attaching photo of the panic (but looks like it is slightly different each time).

I do not want to experiment any more as each panic causes raid resync which is very time consuming.

---

### Post by SergeiFranco on 2011-05-07
submitted bug report:
[https://bugs.launchpad.net/bugs/776936](https://bugs.launchpad.net/bugs/776936)

---

