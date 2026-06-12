---
title: "Ubuntu MAAS boot disk issue."
date: 2015-05-13
forum: Ubuntu Cloud and Juju
---

### Post by j_g2 on 2015-05-13
Hi, 

I'm getting no bootable device.

I am booting creating VM's using KVM mass image used is 14.04LTS, boots PXE fine, gets to the last stages, and console says boot failed, no bootable device, I've tried, raw, qcow2, qcow,  I've tried changing XML file via virsh edit <VM> and changing the disk from vda to sda and changing virtio to scsi. The pxe boot, boots the micro kernel, but then, when I think it's install software on the disk image, it didn't do any of it.

Boot directly from using kvm, does not work either.  The whole KVM/Mass seem to be very temperamental. I followed every link associated KVM no bootable disk and tried what one would consider the obvious things, permission, owner, group etc.

Maybe it's the seabios version, not sure how to change seabios version for virt-manager, I have tried the command line way too btw, it's the same results. After two days of tinkering I've exhausted info channels. 

I just does not work out of the box, as one would expect on an established linux OS.

The XML below.  Thanks. J.

[ATTACH=CONFIG]261962[/ATTACH]


<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh edit ostack1
or other application using the libvirt API.
-->


<domain type='kvm'>
  <name>ostack1</name>
  <uuid>4a6350f1-a176-30c6-8eb9-b8b0fca896da</uuid>
  <memory unit='KiB'>1048576</memory>
  <currentMemory unit='KiB'>1048576</currentMemory>
  <vcpu placement='static'>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/ostack1.qcow2'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </disk>
    <controller type='usb' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <interface type='network'>
      <mac address='34:54:00:8e:47:67'/>
      <source network='default'/>
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
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'/>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </memballoon>
  </devices>
</domain>

---

