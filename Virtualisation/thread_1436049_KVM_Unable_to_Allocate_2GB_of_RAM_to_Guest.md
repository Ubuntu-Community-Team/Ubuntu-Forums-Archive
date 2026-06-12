---
title: "KVM Unable to Allocate 2GB of RAM to Guest"
date: 2010-03-22
forum: Virtualisation
---

### Post by koenigjm on 2010-03-22
I am experiencing a couple prolbems with KVM/QEMU on Ubuntu 8.04 Server LTS (x86_64)and I hope someone here will be able to shed some light as to what I may be missing.

The guest operating system is Windows Server 2003, it was created and installed using the following command:

```

virt-install --connect qemu:///system -n win2k3_2 -r 1024 -f /root/virt_machines/win2k3.qcow2 -s 20 -c /root/iso/win2k3.iso --noautoconsole --os-type windows --os-variant winxp --vnc

```
 
After win2k3 was installed and updated I decided to up the amount of ram listed in /etc/libvirt/qemu/win2k3.xml.  I modified the memory and currentMemory options to 2097152 (2GB).  After this modification I executed the following:

```

virsh define /etc/libvirt/qemu/win2k3.xml
virsh start win2k3

```

And was promptly met with the following error:

```

Connecting to uri: qemu:///system
libvir: QEMU error : QEMU quit during console startup
error: Failed to start domain win2k3

```

Anyone know what may be causing this?  Is it trying to allocate "too much" ram and getting killed by the OS? I see nothing in /var/log/messages.

Relevant System Specs: 
CPU: Core 2 Quad Q9400
RAM: 4GB
OS: Ubuntu 8.04 LTS 64bit

/etc/libvirt/qmeu/win2k3.xml:

```

<domain type='qemu'>
  <name>win2k3</name>
  <uuid>8bf7e4e6-3624-ebe8-3762-b97049e0971a</uuid>
  <memory>2097152</memory>
  <currentMemory>2097152</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
  </features>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='disk'>
      <source file='/root/virt_machines/win2k3.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='file' device='cdrom'>
      <source file='/root/iso/netkvm.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <interface type='network'>
      <mac address='00:11:22:33:44:55'/>
      <source network='default'/>
      <model type='rtl8139'/>
    </interface>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
  </devices>
</domain>

```

---

### Post by koenigjm on 2010-03-22
A little bit more system info.  Below are the results from free...I certainly have enough free for what I am trying to do:

```

free
             total       used       free     shared    buffers     cached
Mem:       4052908     368556    3684352

```

---

