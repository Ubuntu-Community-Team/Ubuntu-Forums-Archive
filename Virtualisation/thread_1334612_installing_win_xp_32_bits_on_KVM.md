---
title: "installing win xp 32 bits on KVM"
date: 2009-11-22
forum: Virtualisation
---

### Post by freazer on 2009-11-22
I've trouble installing windows XP 32 bits on my UBUNTU 9.10 + KVM. The install process hangs on this message 

"The install program is is starting Windows" 

just seconds after launching the install from the XP CD.

Some details about my settings: 
Host: AMD64 TF-20  with UBUNTU 9.10 + KVM + Virtual machine manager
Guest: Windows XP 32 bits SP2

On the same host, I managed to install Windows 7 64 bits without any problem. I can also install Win XP (same install CD) on my VirtualBox (unfortunately the speed is not at the RDV). 

My first thoughts are that the problem is with the config of the virtual machine in KVM. the config XML file is;

<domain type='qemu'>
  <name>WinXP</name>
  <uuid>8361c454-c629-a457-f5db-36b04ce33a62</uuid>
  <memory>524288</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.11'>hvm</type>
    <boot dev='cdrom'/>
  </os>
  <features>
    <pae/>
  </features>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='cdrom'>
      <source file='/home/WinXP.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <disk type='file' device='disk'>
      <source file='/var/lib/libvirt/images/WinXP.img'/>
      <target dev='sda' bus='scsi'/>
    </disk>
    <interface type='network'>
      <mac address='54:52:00:18:9d:5b'/>
      <source network='default'/>
    </interface>
    <serial type='pty'>
      <source path='/dev/pts/2'/>
      <target port='0'/>
    </serial>
    <console type='pty' tty='/dev/pts/2'>
      <source path='/dev/pts/2'/>
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

Is there something wrong with this config?

thnx!

---

### Post by antiram on 2009-11-25
replace the
```

<disk type='file' device='disk'>
<source file='/var/lib/libvirt/images/WinXP.img'/>
<target dev='sda' bus='scsi'/>

```
with 
```

<disk type='file' device='disk'>
      <source file='/var/lib/libvirt/images/WinXP.img'/>
      <target dev='hda' bus='ide'/>
</disk>

```
you could also add a <acpi/> tag after the <pae> tag:

---

