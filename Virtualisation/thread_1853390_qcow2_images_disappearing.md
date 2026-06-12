---
title: "qcow2 images disappearing"
date: 2011-10-02
forum: Virtualisation
---

### Post by filip-k on 2011-10-02
Hello!

I have a problem with dissapearing qcow2 image files on qemu-kvm.
Some time ago I set up qemu-kvm with bridged networking and created vm using vmbuilder, which looks like this:

```
filip@server:~$ virsh dumpxml krab
<domain type='kvm'>
  <name>krab</name>
  <uuid>57604373-ffae-6884-9232-c5efb385c845</uuid>
  <memory>131072</memory>
  <currentMemory>131072</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.14'>hvm</type>
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
      <source file='/home/filip/ubuntu-kvm/krab.qcow2'/>
      <target dev='hda' bus='ide'/>
      <address type='drive' controller='0' bus='0' unit='0'/>
    </disk>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:ec:36:fa'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
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

```Everything worked just fine, vm was running nginx / thin / some rubyon rails apps. After about one day, I noticed that qcow2 image file - /home/filip/ubuntu-kvm/krab.qcow2 simply dissapeared.

After shutting down and starting the vm again, I got the following error: 

```
filip@server:~$ virsh shutdown krab
Domain krab is being shutdown

filip@server:~$ virsh start krab
error: Failed to start domain krab
error: unable to set user and group to '105:115' on '/home/filip/ubuntu-kvm/krab.qcow2': No such file or directory

```Without qcow2 image I was unable to start vm again. 

Since that time I've created several new vms and some of their images have gone away in similar way.

Does anybody know what can cause qcow2 files to disappear? Is it somehow normal operation and I don't know about something, or it's a bug? 

I'm running Ubuntu Server 11.04 64-bit. I would be glad to provide some more information if needed. 

Thanks in advance!

---

### Post by filip-k on 2011-10-02
ok, sorry for false alarm - the problem was caused by misuse of vmbuilder's -o parameter - I just overriten old image with the new one when creating another virtual machine:P

---

