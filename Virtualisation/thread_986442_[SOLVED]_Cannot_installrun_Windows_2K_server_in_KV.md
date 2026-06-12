---
title: "[SOLVED] Cannot install/run Windows 2K server in KVM virt-manager or virsh"
date: 2008-11-18
forum: Virtualisation
---

### Post by pherrera on 2008-11-18
Using kvm from repos on Intrepid i686 (2.6.27-7-server kernel).  Intel Core 2 cpu.

I cannot install/run Win 2K server from virt-manager or using commandline virsh.  Once the machine gets to the point of restarting (after initial install), the screen says "A disk read error occurred" and the cpu goes up to 50% and stays there.

I am able to install and run using the commands:
```
kvm -m 512 -hda win2k-server-polaris.img -cdrom win2kserver.iso -boot d
kvm -m 512 -hda win2k-server-polaris.img -cdrom win2kserver.iso -boot c
```
and
```
kvm -m 512 -hda win2k-server-polaris.img -boot c
```

Both virt-manager/virsh use kvm, right?  Why does using straight kvm work and not virt-manager/virsh??

Here's my machine xml:
```

<domain type='kvm'>
  <name>win2k-server</name>
  <uuid>92a08494-d7a2-bed8-13ea-0b38f89a072f</uuid>
  <memory>524288</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>2</vcpu>
  <os>
    <type arch='i686'>hvm</type>
    <boot dev='hd'/>
  </os>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <source file='/home/dniadmin/win2k-server.img'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <interface type='bridge'>
      <mac address='00:16:36:3c:cc:98'/>
      <source bridge='br0'/>
      <target dev='vnet2'/>
    </interface>
    <serial type='pty'>
      <source path='/dev/pts/9'/>
      <target port='0'/>
    </serial>
    <console type='pty' tty='/dev/pts/9'>
      <source path='/dev/pts/9'/>
      <target port='0'/>
    </console>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='5901' listen='127.0.0.1'/>
  </devices>
</domain>

```

I appreciate any help!!

---

### Post by pred2k on 2008-11-21
I reported the same Problem [here]("http://ubuntuforums.org/showthread.php?t=970385"). But i don't know any solution to run Windows with libvirt.

Because i want to use libvirt with my Linux-Guests - what is working well - i want to know which is the best way to parallel  run/manage my Linux-Guests with libvirt and my Windows-Guests with the simple kvm-command.

---

### Post by pherrera on 2008-11-21
pred2K:  thanks for replying.  After seeing your post, I'm about to give up.  I want to use the same interface to manage all my machines and sadly, at this point, it seems I'm not going to be able with Intrepid.  

After backing up my drive, I installed CentOS 5.2 and was immediately able to install Windows 2000 server.  CentOS uses Xen instead of KVM; KVM may be the new hot thing but I need what works.  Looks like I'll probably be using CentOS as my dom0.  :-k

---

### Post by shin-sasaki on 2009-02-04
When I want to import qemu image file from old PC (dapper) to new PC (hardy), I gut same problem.

I edit ~/.libvirt/qemu/win2k.xml, and it works.

$ pushd ~/.libvirt/qemu
$ diff win2k.xml.org win2k.xml
28c28
<     <graphics type='vnc' port='-1' listen='127.0.0.1'/>
---
>     <graphics type='vnc' port='-1' listen='0.0.0.0'/>

If you can understand japanese, please visit [http://philos0.blog94.fc2.com/blog-entry-15.html](http://philos0.blog94.fc2.com/blog-entry-15.html)

---

