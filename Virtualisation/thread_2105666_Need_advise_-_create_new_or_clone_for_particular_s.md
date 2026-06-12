---
title: "Need advise - create new or clone for particular scenario."
date: 2013-01-16
forum: Virtualisation
---

### Post by fs2307 on 2013-01-16
Greetings.
I need advise on what would be best way of creating particular set of VMs.
This is a strange scenario so it might take a while explain. I have a feeling solution is probably simple one line command that I cannot seem to be able to get.

I have 44 hosts. Eeach of those host will be running ubuntu server with KVM and single VM inside. That VM will be running Fedora 10.

44 hosts are automatically build using PXE boot kickstart script (that already taken care of).
Once they are build i need to create a VM, that VM once started will go to and PXE boot itself and install Fedora 10. (PXE boot script for VM is ready and working.)

I have test VM set and it's seems to be doing what I want.

I am trying to figure out how on the first boot of each host 
create VM with empty drive of the size I need (pretty much raw image) with particular networking setup (2 network cards on each VM mapping to appropriate bridge.) and start it up.

I know how to create this particular VM in virt-manager but so far was not successful in generating it in command line, so I am wondering if cloning it or copying some sample machine and scripting edit of xml file to change mac addresses might be safer way.
Sadly I cannot clone existing disks, I have to generate each VM using PXE.


Here is test vm xml file

[HTML]<domain type='kvm'>
  <name>dot-node</name>
  <uuid>fe7dbdbd-3d51-b6ea-f717-af58ce29b545</uuid>
  <memory>31457280</memory>
  <currentMemory>31457280</currentMemory>
  <vcpu>22</vcpu>
  <os>
    <type arch='x86_64' machine='pc-1.0'>hvm</type>
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
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/var/lib/libvirt/images/dot-node.img'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </disk>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:01:81:14:09'/>
      <source bridge='br1'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <interface type='bridge'>
      <mac address='52:54:01:02:c8:5d'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <input type='mouse' bus='ps2'/>
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
</domain>[/HTML]

---

### Post by fs2307 on 2013-01-16
Looks like easiest way to accomplish this to copy .xml file to new host post install, change mac addresses and then run following :
qemu-img create -f raw /var/lib/libvirt/images/dot-node.img 100g
virsh define node.xml
virsh start

---

