---
title: "Can't connect to virtual machine"
date: 2011-01-06
forum: Virtualisation
---

### Post by majjj on 2011-01-06
Hello once again

I would really appreciate if somebody could answer this one.

So, I have successfully created a virtual machine using [this guide. ]("https://help.ubuntu.com/community/KVM")
Only problem is that I haven't been able to connect the virtual machine in any way. It has definitely started as I can ping to the ip address which I've assigned for it.

I created a VM called hostnameformyvm3 using
```
ubuntu-vm-builder kvm hardy --domain newvm3 --dest newvm3 --arch i386 --hostname hostnameformyvm3 --mem 256 --user user --pass pass --ip 192.168.1.49 --addpkg acpid vim openssh-server --libvirt qemu:///system 
```This should've made possible to connect via ssh, right? When I do nmap to the ip it says that all ports are closed.

It's starting to be really frustrating that I can't connect to it any way. Could someone help me, please.

Edit: when I start the VM syslog says only:
```
Jan  6 15:47:52 ubuntuserver kernel: [ 3087.572787] device vnet0 entered promiscuous mode
Jan  6 15:47:52 ubuntuserver kernel: [ 3087.573773] br0: port 2(vnet0) entering forwarding state
Jan  6 15:48:02 ubuntuserver kernel: [ 3097.897014] vnet0: no IPv6 routers present
```My /etc/libvirt/qemu/hostnameformyvm3.xml
```

<domain type='kvm'>
  <name>hostnameformyvm3</name>
  <uuid>2f7728c4-85e9-f9f0-b1e9-7ca56d458a4e</uuid>
  <memory>262144</memory>
  <currentMemory>262144</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='i686' machine='pc-0.12'>hvm</type>
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
      <source file='/etc/libvirt/qemu/newvm3/tmpwYBA2i.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <interface type='bridge'>
      <mac address='52:54:00:31:fb:cf'/>
      <source bridge='br0'/>
      <model type='virtio'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' listen='127.0.0.1'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
  </devices>
</domain>
```

Edit2: I forgot to tell I'm running Ubuntu server 10.04

---

### Post by majjj on 2011-01-06
Anyone? please...

Is there another way to connect

---

