---
title: "Multicore with libvirt"
date: 2010-07-26
forum: Virtualisation
---

### Post by pmb@novodynamics.com on 2010-07-26
Hello:

I have a virtual machine defined using libvirt. Although I have defined the capabilities of the CPU to include the four cores that my cpu supports, libvirt does not start kvm up with the cores=4 flag for -smp. Has anyone else seen this? Any ideas how to solve it?

Thanks 

pmb

Here's the definition of my virtual machine.

[INDENT][FONT="Courier New"]<domain type='kvm'>
  <name>w7ux64-oem-qcow2</name>
  <uuid>12805a34-e983-9e77-feb0-cad537d8b505</uuid>
  <memory>2097152</memory>
  <currentMemory>2097152</currentMemory>
  <vcpu>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.11'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <cpu match='minimum'>
    <model>core2duo</model>
    <topology sockets='1' cores='4' threads='1'/>
  </cpu>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <source file='/data/kvmimages/w7ux64-oem-qcow2.img'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='file' device='cdrom'>
      <source file='/data/kvmimages/dsl-4.4.10.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <interface type='bridge'>
      <mac address='00:16:36:3d:f5:7a'/>
      <source bridge='br0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target port='0'/>
    </console>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' keymap='en-us'/>
    <sound model='es1370'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
  </devices>
</domain>
[/FONT][/INDENT]

---

