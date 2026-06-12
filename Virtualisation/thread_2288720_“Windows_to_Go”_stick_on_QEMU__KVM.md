---
title: "“Windows to Go” stick on QEMU / KVM"
date: 2015-07-29
forum: Virtualisation
---

### Post by takeawaydave on 2015-07-29
*** Warning - complete KVM newbie ***

Fresh trusty install and I have then installed Qemu and KVM. I have a Windows 8.1 Windows To Go USB stick (Windows 8.1 Enterprise) and would like to run this as a visualized instance. I have done the following so far:
    1. tried to pass through the physical drive to the VM instance
    2. install OVMF to allow UEFI based booting

I achieved the pass through of the physical device by adding the following to my config file:

```
  <devices>
     <emulator>/usr/bin/qemu-system-x86_64</emulator>
     <disk type='block' device='disk'>
       <driver name='qemu' type='raw'/>
       <source dev='/dev/sdi'/>
       <target dev='vdb' bus='virtio'/>
       <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
     </disk>
```

And I also installed OVMF and then added the following:

```
  <os>
     <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
     <loader>OVMF.fd</loader>**
     <boot dev='hd'/>
     <bootmenu enable='yes'/>   
  </os>
```

Am I on the right track here ? Has anyone passed a WTG stick through before ? I gues it would be like passsing any physical disk  directly through.

Thanks !

Edit entire xml file is:
> 
<domain type='qemu'>
  <name>WTG</name>
  <uuid>0509ff4c-6958-2463-321c-512874d8eaac</uuid>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <vcpu placement='static'>8</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <loader>OVMF.fd</loader>
    <boot dev='hd'/>
    <bootmenu enable='no'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/sdi'/>
      <target dev='vdb' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </disk>
    <controller type='usb' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <interface type='network'>
      <mac address='52:54:00:fb:97:4d'/>
      <source network='default'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
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
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </memballoon>
  </devices>
</domain>


The USB WTG stick is confirmed as:

> # lsscsi -v | grep King
[8:0:0:0]    disk    Kingston DT Workspace     KS13  /dev/sdi

The domain starts up, gets to bitlocker, passes bitlocker and then the Windows 8 logo appears for 6/7 seconds and then i resets and goes straight back to the EFI shell.

---

